# python
board = ["-"] *16
board[0] = "1"
board[1] = "2"
board[2] = "3"
board[3] = "4"
board[4] = "5"
board[5] = "6"
board[6] = "7"
board[7] = "8"
board[8] = "9"
board[9] = "10"
board[10] = "11"
board[11] = "12"
board[12] = "13"
board[13] = "14"
board[14] = "15"
board[15] = "16"

validnum = [1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16]
plus = [4,8,12,16]
minus = [1,5,9,13]
numbers = []
player_one_turn = False
player_two_turn = True

#print(board)
def showboard():
    print ((board[0]) + " |" + board[1] + " |" +board[2] + " |" + board[3] )

    print ((board[4]) + " |" + board[5] + " |" +board[6] + " |" + board[7] )

    print ((board[8]) + " |" + board[9] + "|" +board[10] + "|" + board[11] )

    print ((board[12]) + "|" + board[13] + "|" +board[14] + "|" + board[15] )
def player_one():
    player_one_input1 = int(input("please enter a number between 1 - 16: "))
    player_one_input2 = int(input("please enter a number between 1 - 16: "))
    if not (player_one_input1 == player_one_input2 + 4 or player_one_input1 == player_one_input2 - 4 or (player_one_input1 == player_one_input2 - 1  and player_one_input2 not in minus) or (player_one_input1 == player_one_input2 + 1 and player_one_input2 not in  plus)):
        print('invalid input please enter to nums next to each others')
        player_one()

    if player_one_input1 in validnum and player_one_input2 in validnum:
        board[player_one_input1-1] = "x"
        board[player_one_input2-1] = "x"
        validnum.remove(player_one_input1)
        validnum.remove(player_one_input2)
    else:
        print('plese enter a valid number')

def player_two():
    player_one_input1 = int(input("please enter a number between 1 - 16: "))
    player_one_input2 = int(input("please enter a number between 1 - 16: "))
    if not (player_one_input1 == player_one_input2 + 4 or player_one_input1 == player_one_input2 - 4 or (
            player_one_input1 == player_one_input2 - 1 and player_one_input2 not in minus) or (
                    player_one_input1 == player_one_input2 + 1 and player_one_input2 not in plus)):
        print('invalid input please enter to nums next to each others')
        player_one()

    if player_one_input1 in validnum and player_one_input2 in validnum:
        board[player_one_input1 - 1] = "x"
        board[player_one_input2 - 1] = "x"
        validnum.remove(player_one_input1)
        validnum.remove(player_one_input2)
    else:
        print('please enter a valid number')

def check_turn():
   global player_one_turn,player_two_turn
   player_one_turn = not player_one_turn
   player_two_turn = not player_two_turn
   if player_one_turn :
       print("player one turn")
   else:
       print("player two turn")
def check_board ():
    for element in board:
        if element != "x":
            numbers.append(int(element))

    for i in range (0 , len(numbers)-1 ):
        for j in range (i+1,len(numbers)):
            if abs(numbers[i]-numbers[j]) == 4 :
                return True
            if abs(numbers[i]-numbers[j])==1:
                if (numbers[i]!= 4 and numbers[j]!=5) or (numbers[i]!=5 and numbers[j]!=5):
                    if (numbers[i]!= 8 and numbers[j]!=9)or (numbers[i]!=9 and numbers[j]!=8):
                        if (numbers[i]!= 12 and numbers[j]!=13) or (numbers[i]!=13 and numbers[j]!=12):
                            return True
    return False








while True:
    numbers.clear()
    showboard()
    gameContinue = check_board()
    print(numbers)
    if gameContinue:
        check_turn()
        player_one()
        showboard()
    else:
        print(gameContinue)
        if player_one_turn:
            print("player one wins")
        else:
            print("player two wins")
        break
