# PetSmart GraphQL Schema

## Overview

PetSmart does not currently publish a public GraphQL API. This conceptual schema represents the data entities and relationships that would logically underpin PetSmart's retail, services, and pet care operations based on their publicly available website, mobile apps, and documented service offerings.

The schema covers PetSmart's core business domains:

- **Retail**: Products, categories, brands, pricing, inventory, orders, and shipping
- **Store Operations**: Store locations, hours, services, and facilities
- **Pet Services**: Grooming, training, boarding (PetsHotel), doggy day care, and vet clinics (Banfield)
- **Pet Profiles**: Species, breeds, health records, vaccinations, and care history
- **Loyalty Program**: Treats loyalty points, rewards, promotions, and deals
- **Customer Accounts**: Profiles, addresses, payment methods, and order history
- **Adoption**: Rescue animals, adoption events, and animal photos

## Schema Source

Conceptual schema derived from:

- PetSmart website: https://www.petsmart.com
- PetSmart services pages (grooming, training, PetsHotel, Banfield)
- PetSmart Treats loyalty program documentation
- PetSmart adoption and rescue partnership pages
- PetSmart mobile app feature set

## Types Summary

| Domain | Types |
|---|---|
| Store | Store, StoreDetails, StoreHours, StoreServices, StoreLocation |
| Services | PetHotel, Grooming, Training, VetClinic, Banfield, DayPetCare, PetStylist |
| Pets | Pet, PetProfile, Species, Breed, Age, Weight, Health, VaccinationRecord, PetRecord |
| Products | Product, ProductDetails, ProductCategory, ProductBrand, SKU, Price |
| Product Lines | PetFood, Toy, Treat, Supplies, Aquatics, Bird, Reptile, SmallPet, Livestock |
| Adoption | Adoption, RescuedAnimal, AdoptionEvent, AnimalPhoto |
| Appointments | Appointment, GroomingAppointment, HotelBooking, GroomingService, TrainingClass, VetAppointment |
| Customers | PetParent, CustomerProfile, Address, PaymentMethod |
| Loyalty | TreatPoints, LoyaltyCard, RewardPoints, Promotion, Deal |
| Orders | Order, OrderStatus, Shipping, ReturnPolicy |
| Auth | APIKey, Token |

## Queries

- `store(id: ID!)` — fetch a single store by ID
- `stores(zip: String, radius: Int, services: [StoreServiceType])` — find nearby stores
- `product(id: ID!)` — fetch a product by ID
- `products(category: String, brand: String, petType: PetType, limit: Int, offset: Int)` — browse products
- `pet(id: ID!)` — fetch a pet profile
- `petParent(id: ID!)` — fetch a customer account
- `appointments(petParentId: ID!, upcoming: Boolean)` — list appointments
- `adoptionEvents(zip: String, radius: Int)` — find adoption events near a location
- `rescuedAnimals(species: SpeciesType, zip: String)` — browse adoptable animals
- `order(id: ID!)` — get order details
- `orders(petParentId: ID!, status: OrderStatusType)` — list orders for a customer
- `promotions(petParentId: ID)` — active promotions, optionally personalized

## Mutations

- `createPetProfile(input: PetProfileInput!)` — add a pet to an account
- `updatePetProfile(id: ID!, input: PetProfileInput!)` — update pet details
- `bookGroomingAppointment(input: GroomingAppointmentInput!)` — schedule a grooming session
- `bookHotelReservation(input: HotelBookingInput!)` — reserve a PetsHotel stay
- `enrollTrainingClass(input: TrainingClassInput!)` — enroll a pet in training
- `scheduleVetAppointment(input: VetAppointmentInput!)` — book a Banfield vet visit
- `addToCart(productId: ID!, quantity: Int!)` — add a product to cart
- `placeOrder(input: OrderInput!)` — submit an order
- `redeemPoints(petParentId: ID!, points: Int!)` — redeem Treats loyalty points
- `addVaccinationRecord(petId: ID!, input: VaccinationRecordInput!)` — log a vaccine

## File

- Schema: [petsmart-schema.graphql](petsmart-schema.graphql)
