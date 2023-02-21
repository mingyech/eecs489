# Lecture 8: Flow and Congestion Control

Flow control: to make sure *client* is not overwhelmed

Congestion control: to make sure *server* is not overwhelmed

## TCP establishment
Client life cycle: 
```mermaid
stateDiagram
    CLOSED --> SYN_SENT : send SYN
    SYN_SENT --> ESTABLISHED: recieve SYN-ACK, send ACK
    ESTABLISHED --> FIN_WAIT_1: send FIN
    FIN_WAIT_1 --> FIN_WAIT_2: receive ACK
    FIN_WAIT_2 --> TIME_WAIT: receive FIN, send ACK
    TIME_WAIT --> CLOSED: wait 30s
```
Sever lifecyvle:

```mermaid
stateDiagram
    CLOSED --> LISTEN : create a listen socket
    LISTEN --> SYN_RCVD: receive SYN, send SYN-ACK
    SYN_RCVD --> ESTABLISHED: receive ACK, send nothing
    ESTABLISHED --> CLOSED_WAIT: receive FIN, send ACK
    CLOSED_WAIT --> LAST_ACK: send FIN
    LAST_ACK --> CLOSED: receive ACK, send nothing
```

## Flow control
