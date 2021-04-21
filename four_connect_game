# Author: Fabrice Lezzi
# Date: 10-04-2021
# V1.0
# Simple Games
# Four Connect
# Python 3.8
#
# -------- Global Variables -------- #
# Stores the current state of the game
# ----------- 0    1    2    3    4    5
board = b = ['-', '-', '-', '-', '-', '-',  # 0
             '-', '-', '-', '-', '-', '-',  # 6
             '-', '-', '-', '-', '-', '-',  # 12
             '-', '-', '-', '-', '-', '-',  # 18
             '-', '-', '-', '-', '-', '-',  # 24
             '-', '-', '-', '-', '-', '-',  # 30
             '-', '-', '-', '-', '-', '-']  # 36

global player_column
global active_token
global game_still_running


# -------- Methods -------- #
# Displays the board and it's current state
def display_board():
    for i in range(6):
        print(b[i] + ' ' + b[i + 6] + ' ' + b[i + 12] + ' ' + b[i + 18] + ' ' + b[i + 24] + ' ' + b[i + 30] + ' ' + b[
            i + 36] + ' ')


# Get the column from the player and hand it over to place_token()
def get_column_from_player():
    global player_column
    try:
        player_column = int(input("Choose the column in which your stone should go. [1-7]\n: ")) - 1
        if 0 <= player_column <= 6:
            pass
        else:
            print('Wrong input!')
            get_column_from_player()
    except ValueError:
        print('Wrong input!')
        get_column_from_player()
        pass
    return player_column


# Place the token on the board
def place_token(token_column):
    global active_token
    if b[token_column * 6] == '-':
        b[token_column * 6] = active_token
    else:
        print('You can not put this there!')
        get_column_from_player()
        place_token(player_column)
        move_token(player_column)
        display_board()


# move the token down, until it reaches another one or the end of it's column
def move_token(column):
    for i in range(5):
        if b[i + column * 6 + 1] == '-':
            b[i + column * 6 + 1] = b[i + column * 6]
            b[i + column * 6] = '-'
        else:
            pass


def check_win():
    def check_horizontal(token):
        global game_still_running
        for i in range(6):
            if b[i] == b[i + 6] == b[i + 12] == b[i + 18] != '-' \
                    or b[i + 6] == b[i + 12] == b[i + 18] == b[i + 24] != '-' \
                    or b[i + 12] == b[i + 18] == b[i + 24] == b[i + 30] != '-' \
                    or b[i + 18] == b[i + 24] == b[i + 30] == b[i + 36] != '-':
                print(token + ' has won!')
                game_still_running = False
                return game_still_running
            else:
                pass

    def check_vertical(token):
        global game_still_running
        for i in range(37):
            if b[i] == b[i + 1] == b[i + 2] == b[i + 3] != '-':
                print(token + ' has won!')
                game_still_running = False
                return game_still_running

    def check_diagonal(token):
        global game_still_running
        if b[23] == b[28] == b[33] == b[38] != '-'           \
                                                             \
                or b[22] == b[27] == b[32] == b[37] != '-'   \
                or b[17] == b[22] == b[27] == b[32] != '-'   \
                                                             \
                or b[21] == b[26] == b[31] == b[36] != '-'   \
                or b[16] == b[21] == b[26] == b[31] != '-'   \
                or b[11] == b[16] == b[21] == b[26] != '-'   \
                                                             \
                or b[15] == b[20] == b[25] == b[30] != '-'   \
                or b[10] == b[15] == b[20] == b[25] != '-'   \
                or b[5] == b[10] == b[15] == b[20] != '-'    \
                                                             \
                or b[9] == b[14] == b[19] == b[24] != '-'    \
                or b[4] == b[9] == b[14] == b[19] != '-'     \
                                                             \
                or b[3] == b[8] == b[13] == b[18] != '-'     \
                                                             \
                or b[2] == b[9] == b[16] == b[23] != '-'     \
                                                             \
                or b[8] == b[15] == b[22] == b[29] != '-'    \
                or b[1] == b[8] == b[15] == b[22] != '-'     \
                                                             \
                or b[0] == b[7] == b[14] == b[21] != '-'     \
                or b[7] == b[14] == b[21] == b[28] != '-'    \
                or b[14] == b[21] == b[28] == b[35] != '-'   \
                                                             \
                or b[6] == b[13] == b[20] == b[27] != '-'    \
                or b[13] == b[20] == b[27] == b[34] != '-'   \
                or b[20] == b[27] == b[34] == b[41] != '-'   \
                                                             \
                or b[12] == b[19] == b[26] == b[33] != '-'   \
                or b[19] == b[26] == b[33] == b[40] != '-'   \
                                                             \
                or b[18] == b[25] == b[32] == b[39] != '-':
            print(token + ' has won!')
            game_still_running = False
            return game_still_running

    check_horizontal(active_token)
    check_vertical(active_token)
    check_diagonal(active_token)


# Switch token between 'x' and 'o'
def switch_token():
    global active_token

    if active_token == 'x':
        active_token = 'o'
    else:
        active_token = 'x'

    return active_token


# Main game loop and initialising starting player
def main_game():
    global game_still_running
    game_still_running = True

    global active_token
    active_token = 'x'

    display_board()

    # Game loop!
    while game_still_running is True:
        print(active_token + "'s turn!")
        get_column_from_player()
        place_token(player_column)
        move_token(player_column)
        check_win()
        switch_token()
        display_board()


# -------- Main -------- #
if __name__ == '__main__':
    main_game()
