def show_instructions():
    print('''
    RPG Game
    ========
    Commands:
      go [direction]
      get [item]
    ''')

def show_status():
    print('---------------------------')
    print(f'You are in the {current_room}')
    print(f'Inventory: {inventory}')
    if "item" in rooms[current_room]:
        print(f'You see a {rooms[current_room]["item"]}')
    print('---------------------------')

# An inventory, which is initially empty
inventory = []

# A dictionary linking a room to other rooms
rooms = {
    'Hall': {
        'south': 'Kitchen',
        'east': 'Dining Room',
        'item': 'key'
    },
    'Kitchen': {
        'north': 'Hall',
        'item': 'potion'
    },
    'Dining Room': {
        'west': 'Hall',
        'south': 'Garden',
        'item': 'fruit'
    },
    'Garden': {
        'north': 'Dining Room'
    }
}

# Start the player in the Hall
current_room = 'Hall'

show_instructions()

# Loop infinitely
while True:
    show_status()

    # Get the player's next 'move'
    move = ''
    while move == '':
        move = input('> ')

    # Split the move into an action and a direction
    move = move.lower().split()

    # If they type 'go' first
    if move[0] == 'go':
        # Check that they are allowed to move in the direction they want to go
        if move[1] in rooms[current_room]:
            # Set the current room to the new room
            current_room = rooms[current_room][move[1]]
        else:
            print("You can't go that way!")

    # If they type 'get' first
    if move[0] == 'get':
        # If the room contains an item, and the item is the one they want to get
        if "item" in rooms[current_room] and move[1] == rooms[current_room]['item']:
            # Add the item to their inventory
            inventory.append(move[1])
            # Display a helpful message
            print(f'{move[1]} got!')
            # Remove the item from the room
            del rooms[current_room]['item']
        else:
            # Tell them they can't get that item
            print(f"Can't get {move[1]}!")

    # If a player enters a room with a monster
    if 'item' in rooms[current_room] and rooms[current_room]['item'] == 'monster':
        print('A monster has got you... GAME OVER!')
        break

    # Define how a player can win
    if current_room == 'Garden' and 'key' in inventory and 'potion' in inventory:
        print('You escaped the house with the ultra rare key and magic potion... YOU WIN!')
        break# Auto detect text files and perform LF normalization- 👋 Hi, I’m @Salah2010gohary
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...

<!---
Salah2010gohary/Salah2010gohary is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
