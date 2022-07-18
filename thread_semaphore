#include <stdio.h>
#include <stdlib.h>
#include <pthread.h>
#include <semaphore.h>

sem_t semaforo;
int ticket = 1000;

// numero indisponivel
int get_ticket(){
    sem_wait(&semaforo);
    return ticket;
}

// numero fica disponivel quando chama
void *return_ticket(int i){
    sem_post(&semaforo);
    int ret_ticket = get_ticket();
    printf("Ticket recebido = %d\n", ret_ticket);
}

// loop com 2 threads:
// dorme um segundo -> get ticket
// dorme outro segundo -> return ticket

int main(void){
    sem_init(&semaforo, 0, 1);

    pthread_t ret_t;

    pthread_create(&ret_t, NULL, return_ticket, NULL);

    return 0;
}
