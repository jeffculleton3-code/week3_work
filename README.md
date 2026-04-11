week3_work

Hello_mpi takes a larger amount of real time to run than hello_mpi_serial, however, once hello_mpi runs with around 8 processes, the sum of the user and system time starts to exceed the real time which indicates parallel processing is occurring. 

Describe proof.c:
main(): The function does some initialisation operations for error handilng, numerical argument, MPI, rank and size, and uses functions to check the arguments. The communicator universe size and what task to carry out. It then finalises the MPI environment.
root_task(): The function initialises the transmission variables for MPI_Recv and a variable for final output. The MPI_Recv function is then used in a loop to sum received messages. It then outputs the final result. 
client_task(): The function initialises transmission variables for MPI_Send. It creates a destination variable and calculates the message. The function ends by sending the message with MPI_Send.
check_args(): The function first initialises the numerical argument variable. It then checks to make sure there are only two arguments, the program name and numerical argument. It then reads the program name and converts the second character to an integer and declares that to be the new numerical argument. The function raises errors if there are not the correct number of arguments. 
check_uni_size(): The function sets a minimum universe size and then makes sure the universe size is greater than this minimum, meaning there are a sufficient number of processes to communicate with.
check_task(): There are two separate tasks carried out by each of the types of nodes: the client and the root. The clients (ranks >0) send the results of their calculation, while the root receives them, then adds them together.

Mathematical operation: a mathematical formula that achices the same result is multiplying the given number by the sum of all natural numbers that come before. 

S=  ((n-1)((n-1)+1)))/2  * m
Where n is the first input and m is the second input.

Describe vector_serial:
main(): First initialises numerical argument. Creates a vector variable by using the memory allocation function and initialises every element to zero. It then sums the vector and prints the sum.
Sum_vector(): creates a sum variable and then iterates through the elements of the vector to add them up.
Initialise_vector(): iterates through each element of the vector and sets the elements to the initials value.
Print_vector(): iterates through each element of the vector and prints the elements to the screen.
Check_args(): similar to the one from proof.c where it just makes sure that there are the correct number of arguments.

Added to vector serial to make the vector not trivial:
 for (int i = 0; i < num_arg; i++) 
        {
                my_vector[i] = i;
        }
A parallelised version of the code was made called vector_sum_parallel.c.

Both of these programs very quickly overflow (vector size of about 66000) and the parallel version doesnt complete in real time faster than the serial version before an overflow. 
