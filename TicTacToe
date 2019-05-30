#La Mar Holmes
from IPython.display import clear_output
import random
#get player
player1 = input("Please Choose X or O: ").upper()
while player1 != 'X' and player1 !='O':
	player1 = input("Please Choose X or O: ").upper()

computer = 'X' if player1 == 'O' else 'O'
winner = ''
playerMoves = []
compMoves = []
whoPlayed = []
turns = 0
PlayBoard = [' ']*10



def whoFirst():
	person = random.randint(1,2)
	return 'player' if person == 1 else 'computer'

def player_input():
	if len(whoPlayed) == 0 or whoPlayed[len(whoPlayed)-1] != 'player':
		move = input("Please choose between 1 and 9: ")
		move = int(move)
		while move in PlayBoard and (move <= 1 and move >= 9):
			move = input(int("Please choose between 1 and 9"))
		playerMoves.append(move)
		whoPlayed.append('player')
		place_marker(PlayBoard, player1, move)
		if turns > 5:
				if checkWinner(playerMoves):
					winner = 'player'
					print('Winner Player1')
		return True
	return False

def comp_input():
	if len(whoPlayed) == 0 or whoPlayed[len(whoPlayed)-1] != 'computer' :
		if turns <= 1:
			startSpots = [1,3,5,7,9]
			computerMove = startSpots[random.randint(1,len(startSpots)-1)]
			while  PlayBoard[computerMove] != ' ':
				computerMove = startSpots[random.randint(1,len(startSpots)-1)]
			whoPlayed.append('computer')
			compMoves.append(computerMove)
			place_marker(PlayBoard, computer, computerMove)
			if turns > 5:
				if checkWinner(compMoves):
					winner = 'computer'
			return True

		if whoPlayed[len(whoPlayed)-1] != 'computer':
			computerMove = random.randint(1,9)
			while PlayBoard[computerMove] != ' ':
				computerMove = random.randint(1,9)
			compMoves.append(computerMove)
			whoPlayed.append('computer')
			place_marker(PlayBoard, computer, computerMove)
			return True
	return False

def place_marker(board, marker, position):
	board[position] = marker

def display_board(board):
    print(board[1]+ '|' + board[2] + '|'+ board[3])
    print('- '+'- '+'-')
    print(board[4]+ '|' + board[5] + '|'+ board[6])
    print('- '+'- '+'-')
    print(board[7]+ '|' + board[8] + '|'+ board[9])


#Checking the winning combos
winningMoves = [[1,2,3],[1,4,7],[1,5,9],[2,5,8],[3,5,7],[3,6,9],[4,5,6],[7,8,9]]
def checkWinner(moves):
	moves.sort()
	for x in range(0,len(winningMoves)):
		score = 0
		for y in range(0,len(winningMoves[x])):
			if winningMoves[x][y] in moves:
				score+=1
				if score == 3:
					return True
	return False

#Start the game over
def replay_game():
	replay = input('Do you want to replay (Y/N)')
	while replay != 'Y' and replay != 'N' and replay != 'Yes' and replay != 'N':
		replay = input('Do you want to replay (Y/N)')
	if replay == 'Y' or replay == 'Yes':
		return True
	return False

while turns <= 9 or winner == '':
	if turns == 9:
		winner = 'Draw'
	if winner:
		break

	print(PlayBoard)

	if turns == 0:
		start = whoFirst()
		clear_output()
		display_board(PlayBoard)
		if start == 'computer':
			print('Computer goes first')
			comp_input()
			clear_output()
			display_board(PlayBoard)
			turns+=1
		if start == 'player':
			print('Player goes first')
			player_input()
			turns+=1

	player_input()
	turns+=1
	if turns >= 5:
		print('Checking...')
		if checkWinner(playerMoves):
			winner = 'Player'
			clear_output()
			display_board(PlayBoard)
			print('The Winner is',winner)
			if replay_game():
				playerMoves = []
				compMoves = []
				whoPlayed = []
				turns = 0
				PlayBoard = [' ']*10
				winner = ''
			else:
				break

	comp_input()
	clear_output()
	display_board(PlayBoard)
	turns+=1
	if turns >= 5:
		print('Checking...')
		if checkWinner(compMoves):
			winner = 'computer'
			clear_output()
			display_board(PlayBoard)
			print('The Winner is',winner)
			if replay_game():
				playerMoves = []
				compMoves = []
				whoPlayed = []
				turns = 0
				PlayBoard = [' ']*10
				winner = ''
			else:
				break

	print('Computer: ', computer,compMoves)
	print('Player: ', player1,playerMoves)


