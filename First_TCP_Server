#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>

#include <sys/types.h>
#include <sys/socket.h>

#include <netinet/in.h>

int main(int argc, char **argv)
{	
	char server_message[] ="HTTP/1.1 200 OK\r\nContent-Type: text/html\r\nConnection: reset\r\n\r\n<h1>Welcome to my server b. You now have permission to sock my ass</h1>";
	
	int x = 1;
	int z = 2;
	
	//char server_message1[] = "HTTP/1.1 200 OK\r\nContent-Type: text/html\r\nConnection: reset\r\n\r\n<h1>"%d"</h1>",&z;
	//char server_message[] = "http/1.1 200 ok\r\ncontent-type: "
	
	int server_socket;
	server_socket = socket(AF_INET, SOCK_STREAM, 0);
		
	printf("got1\n");
	
	// define server adsress
	struct sockaddr_in server_address;
	server_address.sin_family = AF_INET;
	
	server_address.sin_addr.s_addr = inet_addr("0.0.0.0");
	server_address.sin_port = htons(8080);
	//server_address.sin_port = htons(9002);
	
	printf("got2\n");
	
	//bind the socket to spec IP and port
	bind(server_socket, (struct sockaddr * ) &server_address, sizeof(server_address));

	listen(server_socket, 5); // i detta fall spelar 5 siffran ingen roll
			
	for(;;){
	    int client_socket = accept(server_socket, NULL, NULL);
	    printf("accepted\n");
		
		// lägg in fork för fler trådar
		
		char recv_buf[1024];
		
		read(client_socket, recv_buf, sizeof(recv_buf));
				
		//send the message
		send(client_socket, server_message, sizeof(server_message), 0);
				
		//close the socket
		close(client_socket);
	}
	
	
	return 0;
}
