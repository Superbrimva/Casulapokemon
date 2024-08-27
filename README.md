# Casulapokemon

import random

# Introduction function
def display_intro():
    print("Welcome to the Pokémon Battle Simulator!")
    print("\nChoose your Pokémon to battle a randomly selected opponent.")
    print("You can continue battling or exit the game at any time.")
    print("Let's begin!\n")

# Class definition for a Pokémon
class Pokemon:
    def __init__(self, name, base_power):
        self.name = name
        self.base_power = base_power

    def calculate_final_power(self):
        return self.base_power + random.randint(-5, 5)

# Function for choosing the user's Pokémon
def get_user_pokemon():
    pokemon_list = [
        Pokemon("Pikachu", 50),
        Pokemon("Charmander", 55),
        Pokemon("Bulbasaur", 60),
        Pokemon("Squirtle", 50),
        Pokemon("Jigglypuff", 50),
        Pokemon("Eevee", 55),
        Pokemon("Snorlax", 160),
        Pokemon("Gengar", 65),
        Pokemon("Machamp", 90),
        Pokemon("Mewtwo", 110)
    ]

    print("SELECT YOUR POKÉMON:")
    for index, pokemon in enumerate(pokemon_list, 1):
        print(f"{index}: {pokemon.name} (Base Power: {pokemon.base_power})")

    while True:
        choice = input("Enter the number of your choice: ")
        if choice.isdigit() and 1 <= int(choice) <= len(pokemon_list):
            return pokemon_list[int(choice) - 1]
        print("Invalid selection. Please enter a valid number.")

# Function to randomly choose the opponent's Pokémon
def get_opponent_pokemon():
    return random.choice([
        Pokemon("Pikachu", 50),
        Pokemon("Charmander", 55),
        Pokemon("Bulbasaur", 60),
        Pokemon("Squirtle", 50),
        Pokemon("Jigglypuff", 50),
        Pokemon("Eevee", 55),
        Pokemon("Snorlax", 160),
        Pokemon("Gengar", 65),
        Pokemon("Machamp", 90),
        Pokemon("Mewtwo", 110)
    ])

# Function to simulate a battle between user and opponent Pokémon
def simulate_battle(user_pokemon, opponent_pokemon):
    user_power = user_pokemon.calculate_final_power()
    opponent_power = opponent_pokemon.calculate_final_power()

    print(f"\nYour Pokémon: {user_pokemon.name} (Final Power: {user_power})")
    print(f"Opponent's Pokémon: {opponent_pokemon.name} (Final Power: {opponent_power})")

    if user_power > opponent_power:
        print(f"You win! {opponent_pokemon.name} is defeated!")
        user_pokemon.base_power += opponent_pokemon.base_power
        print(f"{user_pokemon.name}'s new base power is {user_pokemon.base_power}\n")
        return "win"
    else:
        print(f"You lose! {user_pokemon.name} is defeated by {opponent_pokemon.name}.\n")
        return "loss"

# Main game function
def run_game():
    display_intro()
    user_pokemon = get_user_pokemon()

    while True:
        opponent_pokemon = get_opponent_pokemon()
        simulate_battle(user_pokemon, opponent_pokemon)

        if input("Press 'x' to exit or press c to continue: ").lower() == 'x':
            print("Thank you for playing!")
            break

        if input("Do you want to keep your Pokémon or select a new one? (k: keep, s2
        : select new): ").lower() == 's':
            user_pokemon = get_user_pokemon()

# Start the game
if __name__ == "__main__":
    run_game()

    
