# FelobaterWael
package com.mycompany.hotelreservationsystem;

public class Room {
    int roomNumber;
    String type;
    boolean booked;

    Room(int roomNumber, String type) {
        this.roomNumber = roomNumber;
        this.type = type;
        this.booked = false;
    }
}

package com.mycompany.hotelreservationsystem;

import java.util.ArrayList;
import java.util.Scanner;

/**
 *
 * @author ASD
 */
public class HotelReservationSystem {

    static ArrayList<Room> rooms = new ArrayList<>();

    public static void main(String[] args) {
      Scanner input = new Scanner(System.in);

        rooms.add(new Room(101, "Standard"));
        rooms.add(new Room(102, "Deluxe"));
        rooms.add(new Room(103, "Suite"));

        while (true) {

            System.out.println("\n=== Hotel Reservation System ===");
            System.out.println("1. View Rooms");
            System.out.println("2. Book Room");
            System.out.println("3. Cancel Booking");
            System.out.println("4. Exit");
            System.out.print("Enter your choice:");

            int choice = input.nextInt();

            switch (choice) {
                case 1:
                    displayRooms();
                    break;

                case 2:
                    System.out.print("Enter Room Number: ");
                    int bookRoom = input.nextInt();
                    bookRoom(bookRoom);
                    break;

                case 3:
                    System.out.print("Enter Room Number: ");
                    int cancelRoom = input.nextInt();
                    cancelBooking(cancelRoom);
                    break;

                case 4:
                    System.out.println("Thank you!");
                    System.exit(0);
            }
        }
    }
    static void displayRooms() {

        for (Room room : rooms) {

            System.out.println(
                    "Room " + room.roomNumber +
                    " | Type: " + room.type +
                    " | Booked: " + room.booked);
        }
    }

    static void bookRoom(int number) {

        for (Room room : rooms) {

            if (room.roomNumber == number) {

                if (!room.booked) {
                    room.booked = true;
                    System.out.println("Room booked successfully!");
                } else {
                    System.out.println("Room already booked!");
                }
                return;
            }
        }

        System.out.println("Room not found!");
    }
    static void cancelBooking(int number) {

        for (Room room : rooms) {

            if (room.roomNumber == number) {

                if (room.booked) {
                    room.booked = false;
                    System.out.println("Booking cancelled successfully!");
                } else {
                    System.out.println("Room is not booked!");
                }
                return;
            }
        }

        System.out.println("Room not found!");
            }
    }

package com.mycompany.aichatbot;

import java.util.Scanner;

public class AIChatbot {

    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);

        System.out.println("=== AI Chatbot ===");
        System.out.println("Type 'bye' to exit");

        while (true) {

            System.out.print("You: ");
            String message = input.nextLine().toLowerCase();

            if (message.contains("hello") || message.contains("hi")) {
                System.out.println("Bot: Hello! How can I help you?");
            }

            else if (message.contains("your name")) {
                System.out.println("Bot: I am CodeAlpha AI Chatbot.");
            }

            else if (message.contains("how are you")) {
                System.out.println("Bot: I am fine. Thanks for asking!");
            }

            else if (message.contains("java")) {
                                System.out.println("Bot: Java is a powerful programming language.");
            }

            else if (message.contains("bye")) {
                System.out.println("Bot: Goodbye!");
                break;
            }

            else {
                System.out.println("Bot: Sorry, I don't understand.");
            }
            }
    }
}
