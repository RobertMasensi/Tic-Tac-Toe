# Tic-Tac-Toe
First Text Based Project built with Python
from IPython.display import clear_output

def display_board(board):
    clear_output()
    
   print('   |   |')
   print(' ' + board[7] + ' | ' + board[8] + ' | ' + board[9])
   print('   |   |')
   print('-----------')
   print('   |   |')
   print(' ' + board[4] + ' | ' + board[5] + ' | ' + board[6])
   print('   |   |')
   print('-----------')
   print('   |   |')
   print(' ' + board[1] + ' | ' + board[2] + ' | ' + board[3])
   print('   |   |')
    
   test_board=['#','X','X','X','O','','X','X','','O']
   display_board(test_board)
    
def player_input():
   marker=''
   #Now we will assign a marker to specific value for each player.
    
  while marker!='X' and marker!='O':
      marker=input('Player1, choose X or O: ')
        
   player1=marker
    
   if player1=='X':
       player2='O'
   else:
       player2='X'
            
   return (player1, player2)
    
   (player1_marker, player2_marker)=player_input()
    
def place_marker(board, marker, position):
    board[position]=marker
    
    place_marker(test_board,'$',8)
    
    
    display_board(test_board)
    
def win_check(board, mark):
    if board[1]==board[2]==board[3]==mark:
        return True
    if board[4]==board[5]==board[6]==mark:
        return True
    if board[7]==board[8]==board[9]==mark:
        return True
    if board[1]==board[4]==board[7]==mark:
        return True
    if board[2]==board[5]==board[8]==mark:
        return True
    if board[3]==board[6]==board[9]==mark:
        return True
    if board[1]==board[5]==board[9]==mark:
        return True
    if board[3]==board[5]==board[7]==mark:
        return True
    else:
        return False
        
   win_check(test_board,'X')
     
   import random

def choose_first():
    goes_first=random.randint(1,2)
      
    if goes_first==1:
    
       return('Player 1')
    else:
       return('Player 2') 
    return goes_first
   choose_first()
      
def space_check(board, position):
    
         return board[position]==''
        
space_check(test_board,8)
      
def full_board_check(board):
    for n in range(1,10):
        if space_check(board,n):
            return False
    return True
full_board_check(test_board)   
      
def player_choice(board):
    position=0
   
    while position not in [1,2,3,4,5,6,7,8,9] or not space_check(board, position):
        position=int(input('Please select a position: (1-9)'))
        
    return position      
 player_choice(test_board)
       
def replay():
    return(input('Would you like to play again? Yes or No?'))
replay()          
        
print('Welcome to Tic Tac Toe!')

while True:
   the_board=['']*10
    
   player1_marker, player2_marker=player_input()
    
   turn=choose_first()
   print(turn + ' will go first!')
    
   play_game=input('Ready to play? y or n?')
        
   if play_game=='y':
       game_on=True
   else:
        game_on=False
        
   while game_on:
        
      if turn=='Player 1':
    
            
           ## Display the board
           display_board(the_board)
           # Make a selection
           position=player_choice(the_board)
           ###  Place the selection on the board
           place_marker(the_board, player1_marker, position)
            
           if win_check(the_board, player1_marker):
               display_board(the_board)
               print('Player 1 has Won!')
               break
           else:
               if full_board_check(the_board):
                   display(the_board)
                   print('The Game is Tied!')
                   break
               else:
                   turn = 'Player 2
                   
   else:
            # Player2's turn.
            display_board(the_board)
            # Choose a position
            position = player_choice(the_board)
            # Place the marker on the position
            place_marker(the_board, player2_marker, position)
            
            if win_check(the_board, player2_marker):
                display_board(the_board)
                print('Player 2 has Won!')
                break
            else:
                if full_board_check(the_board):
                    display_board(the_board)
                    print('The Game is Tied!')
                    break
                else:
                    turn='Player 1'
   if not replay():
       break
