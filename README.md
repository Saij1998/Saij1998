- 👋 Hi, I’m @Saij1998
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...

<!---
Saij1998/Saij1998 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
package com.easyrentals.ui;

import java.util.Comparator;
import java.util.List;
import java.util.stream.Collectors;

import com.easyrentals.model.Bike;
import com.easyrentals.service.BikeService;

public class UserInterface {

    public static void main(String[] args) {
        // Bike Operations
        BikeService bikeService = new BikeService();
        List<Bike> bikes = bikeService.getAllBikes();

        // 1. Display all available bikes
        System.out.println("Available Bikes for Rent:");
        for (Bike bike : bikes) {
            System.out.println("Bike ID: " + bike.getBikeId());
            System.out.println("Bike Name: " + bike.getBikeName());
            System.out.println("Company Name: " + bike.getCompanyName());
            System.out.println("Serial Number: " + bike.getSerialNumber());
            System.out.println("Rent Price: " + bike.getRentPrice());
            System.out.println("-----------------------------------");
        }

        // 2. Bikes sorted in ascending order of rent price
        System.out.println("\nBikes in ascending order of Rent Price:");
        bikes.stream()
                .sorted(Comparator.comparing(Bike::getRentPrice))
                .forEach(bike -> {
                    System.out.println("Bike ID: " + bike.getBikeId() +
                                       ", Name: " + bike.getBikeName() +
                                       ", Rent Price: " + bike.getRentPrice());
                });

        // 3. Bikes from a specific company (e.g., Hero)
        System.out.println("\nBikes from 'Hero':");
        bikes.stream()
                .filter(bike -> "Hero".equalsIgnoreCase(bike.getCompanyName()))
                .forEach(bike -> {
                    System.out.println("Bike ID: " + bike.getBikeId() +
                                       ", Name: " + bike.getBikeName() +
                                       ", Rent Price: " + bike.getRentPrice());
                });

        // 4. Bikes with rent price above a threshold (e.g., >1000)
        System.out.println("\nBikes with Rent Price > 1000:");
        bikes.stream()
                .filter(bike -> bike.getRentPrice() > 1000)
                .forEach(bike -> {
                    System.out.println("Bike ID: " + bike.getBikeId() +
                                       ", Name: " + bike.getBikeName() +
                                       ", Rent Price: " + bike.getRentPrice());
                });

        // 5. Top 3 expensive bikes
        System.out.println("\nTop 3 Expensive Bikes:");
        bikes.stream()
                .sorted(Comparator.comparing(Bike::getRentPrice).reversed())
                .limit(3)
                .forEach(bike -> {
                    System.out.println("Bike ID: " + bike.getBikeId() +
                                       ", Name: " + bike.getBikeName() +
                                       ", Rent Price: " + bike.getRentPrice());
                });
    }
}
