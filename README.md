import java.util.Scanner;
public class BullyAlgorithm {
 class Process {
 int id;
 boolean active;
 public Process(int id) {
 this.id = id;
 active = true;
 }
 }
 int totalProcesses;
 Process[] processes;
 public BullyAlgorithm(int totalProcesses) {
 this.totalProcesses = totalProcesses;
 processes = new Process[totalProcesses];
 for (int i = 0; i < totalProcesses; i++) {
 processes[i] = new Process(i);
 }
 }
 public void election(int initializedProcess) {
 System.out.println("Process " + processes[initializedProcess].id + " initiates the election.");
 int maxId = processes[initializedProcess].id;
 int maxIndex = initializedProcess;
 for (int i = initializedProcess + 1; i < totalProcesses; i++) {
 if (processes[i].active) {
 if (processes[i].id > maxId) {
 System.out.println("Process " + processes[i].id + " receives election message from process " + 
processes[initializedProcess].id);
 maxId = processes[i].id;
 maxIndex = i;
 }
 }
}
 if (maxIndex != initializedProcess) {
 System.out.println("Process " + processes[maxIndex].id + " is the new coordinator.");
 for (int i = maxIndex + 1; i < totalProcesses; i++) {
 if (processes[i].active) {
 System.out.println("Process " + processes[i].id + " receives coordinator message from process " + 
processes[maxIndex].id);
 }
 }
 } else {
 System.out.println("Process " + processes[initializedProcess].id + " is the coordinator.");
 }
 }
 public static void main(String[] args) {
 Scanner input = new Scanner(System.in);
 System.out.print("Enter the number of processes: ");
 int totalProcesses = input.nextInt();
 BullyAlgorithm algorithm = new BullyAlgorithm(totalProcesses);
 System.out.print("Enter the ID of the process that initiates the election: ");
 int initializedProcess = input.nextInt();
 algorithm.election(initializedProcess);
 input.close();
 }
}



The given code implements the Bully Algorithm for leader election in a distributed 
system.
1. The Process class defines a process with an ID and a boolean active flag that 
indicates whether the process is currently participating in the election.
2. The BullyAlgorithm class initializes an array of Process objects, with each 
object representing a process in the distributed system. The total number of 
processes is passed as a parameter to the constructor.
3. The election method is the main algorithm that is called when a process 
initiates an election. The method takes as input the ID of the process that 
initiated the election.
4. The method first prints out a message indicating which process initiated the 
election.
