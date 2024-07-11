import java.util.Scanner;
class Ticket {
    String passengerName;
    int age;
    String starting;
    String destination;
    int ticketNumber;

    public Ticket(String passengerName, int age, String starting, String destination, int ticketNumber) {
        this.passengerName = passengerName;
        this.age = age;
        this.starting = starting;
        this.destination = destination;
        this.ticketNumber = ticketNumber;
    }

    public void displayTicket() {
        System.out.println("Ticket Details:");
        System.out.println("Passenger Name: " + passengerName);
        System.out.println("Age: " + age);
        System.out.println("Starting: " + starting);
        System.out.println("Destination: " + destination);
        System.out.println("Ticket Number: " + ticketNumber);
    }
}

class SelectionTrain {
    int selectTrain(int j) {
        String trainName = "";
        String startingStation = "";
        int baseFareSleeper = 0;
        int baseFareAC = 0;
        switch (j) {
            case 1: {
                trainName = "Rajdhani Express";
                startingStation = "Sealdah Station";
                baseFareSleeper = 2099;
                baseFareAC = 1560;
                break;
            }
            case 2: {
                trainName = "Satabdi Express";
                startingStation = "Howrah Station";
                baseFareSleeper = 1801;
                baseFareAC = 981;
                break;
            }
            case 3: {
                trainName = "Humsafar Express";
                startingStation = "Kolkata Chitpur Express";
                baseFareSleeper = 2199;
                baseFareAC = 1780;
                break;
            }
            case 4: {
                trainName = "Garib-Rath Express";
                startingStation = "Sealdah Station";
                baseFareSleeper = 1759;
                baseFareAC = 1200;
                break;
            }
            case 5: {
                trainName = "Duronto Express";
                startingStation = "Santraganchi Station";
                baseFareSleeper = 2205;
                baseFareAC = 1905;
                break;
            }
            default:
                System.out.println("Enter Correct choice.....\n");
                return 0;
        }

        // Display train details
        System.out.println("Train Selected: " + trainName);
        System.out.println("Starting Station: " + startingStation);

        // Call function to calculate fare
        int fare = calculateFare(baseFareSleeper, baseFareAC, j);
        System.out.println("Total Fare: " + fare);

        return fare;
    }

    
    int calculateFare(int baseFareSleeper, int baseFareAC, int trainNumber) {
        int classChoice;
        Scanner sc = new Scanner(System.in);
        System.out.println("\t\tEnter Your Choice......\n");
        System.out.println("\t\t1. Sleeper Class....\n");
        System.out.println("\t\t2. A.C Class.......\n");
        classChoice = sc.nextInt();
        switch (classChoice) {
            case 1: {
                return baseFareSleeper;
            }
            case 2: {
                return baseFareAC;
            }
            default:
                System.out.println("Invalid Choice. Defaulting to Sleeper Class.");
                return baseFareSleeper;
        }
    }
}


class SeatBook {
    void displaySeatMatrix() {
        System.out.println("\t           -:SEAT MATRIX:-        \n");
        System.out.println("\t(U)    (M)        (L)    (L)           (U)\n\n");
        System.out.println("\t01    02        03    04        05 \n\n");
        System.out.println("\t06    07        08    09        10 \n");
        System.out.println("\t11    12        13    14        15\n\n");
        System.out.println("\t16    17        18    19        20\n");
        System.out.println("\t21    22        23    24        25\n\n");
        System.out.println("\t26    27        28    29        30\n");
        System.out.println("\t31    32        33    34        35\n\n");
        System.out.println("\t36    37        38    39        40\n");
        System.out.println("\t41    42        43    44        45\n\n");
        System.out.println("\t46    47        48    49        50\n");
        System.out.println("\t51    52        53    54        55\n\n");
        System.out.println("\t56    57        58    59        60\n");
    }
}


public class RailwayTicketReservationSystem {

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.println("Welcome to Railway Ticket Reservation System");
        System.out.println("ENTER THE NUMBER OF PASSENGERS");
        int numberOfPassengers = sc.nextInt();
        sc.nextLine(); // Consume newline character after reading integer

        String[] names = new String[numberOfPassengers];
        for (int i = 0; i < numberOfPassengers; i++) {
            System.out.print("Enter Passenger Name " + (i + 1) + ": ");
            names[i] = sc.nextLine();
        }

        System.out.print("Enter Passenger Age: ");
        int age = sc.nextInt();
        sc.nextLine(); // Consume newline character after reading integer

        System.out.print("Enter starting point: ");
        String startingPoint = sc.nextLine();

        System.out.print("Enter Destination point: ");
        String destination = sc.nextLine();

        System.out.println("\t\tThe Following Trains Are Available.....\n");
        System.out.println("\t\t  1. Rajdhani Express...." + ".....10:00" + "a.m........Sealdah Station\n");
        System.out.println("\t\t2. Satabdi Express..." + ".......05:00 " + "p.m........Howrah Station\n");
        System.out.println("\t\t3. Humsafar Express..." + ".......11:00 " + "p.m........Kolkata Chitpur" + " Station\n");
        System.out.println("\t\t4. Garib-Rath Express" + ".........05:00 " + "p.m........Sealdah Station\n");
        System.out.println("\t\t5. Duronto Express..." + ".........07:00 " + "a.m.........Santraganchi" + "Station\n");

        int trainChoice = sc.nextInt();
        System.out.println("----------------------------");
        SelectionTrain selectionTrain = new SelectionTrain();
        int totalFare = selectionTrain.selectTrain(trainChoice);
        System.out.println("----------------------------");

        SeatBook seatBook = new SeatBook();
        seatBook.displaySeatMatrix();
        System.out.println("----------------------------");

     
        int ticketNumber = 12345; // Dummy ticket number

      
        Ticket ticket = new Ticket(names[0], age, startingPoint, destination, ticketNumber);
        ticket.displayTicket();

        sc.close();
    }
}
