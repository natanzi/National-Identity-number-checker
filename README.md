# National-Identity-number-checker
National Identity checking - Code melli
#The Iranian identity card is the primary identity document in Iran, and in some cases, we need to validate digits to get access or issue the token.
#code
attempts = 0
while True:
    I_N_C = input('Enter Your National code: ')
    if len(I_N_C) == 10:
        pass
        break
    elif len(I_N_C) >= 10 or len(I_N_C) <= 10:
        attempts += 1
        print(f'Your attempts so far was {attempts} times. Entered National code is not equal to digits, try again...')
        if attempts >= 3:
            print(f'you have tried {attempts} times , ...)')
            if attempts == 10:
                print(f'no need to try more...)')
                break

if len(I_N_C) == 10:
    last_digit = int(I_N_C[-1])
    result = ''
    text = ''
    text_sum = 0
    for i in range(len(I_N_C)-1):
        text = text + f'({I_N_C[i]}*{-i + len(I_N_C)}) + '
        result = sum(i * int(c) for i, c in enumerate(I_N_C[-2::-1], 2))
        text_sum = text_sum + (int(I_N_C[i]) * (-i + len(I_N_C)))
    text = text[:len(text)-3]
    modulus = text_sum % 11

    def Output():
        if modulus + last_digit == 11 and modulus >= 2:
            return f'Entered National code {I_N_C} is correct...)\n'
        elif 2 >= modulus == last_digit:
            return f'Entered National code {I_N_C} is correct...)\n'
        else:
            return f'Error, National code {I_N_C} is not correct.\n'

    Output = Output()
    output = open('data.txt', 'a')
    output.write(f'''First, we calculate: {text}.
The sum is: {text_sum}.
Then we calculate the remainder of the division "text_sum % 11" is {modulus}.
Now we\'ll check if National code is correct in the next line:
{Output}\n\n''')

print('The End of the Script')
