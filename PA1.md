## Project Assignment 1

# Approach:
Initially we take filenames as inputs from the user. We then read the file and check if the length of the data received from the file is of equal length if not then it cannot be compared. I also validated for the shift to be in range (1, length(sequence)-1). Further to this if the sequence has other characters than A,C,G,T , the code mentions the error and exits the code. After all the criterias are satisfied, we go ahead and check for matches. We see what method the user has choosen and according to that we choose which method needs to be called. If user wants to do score comparison, we take the sequence input and check each character at a time and once we get for one shift I change remove the choose string from index+i and this keeps comparing with the other sequence. This is done for both the sequences and then checked for score. For contiguous score, we pass the two sequences and check for characters to match, if we get a matcg we increase the counter and check for the length of the sequence if it is less than length(sequence)-1 and the we check for next position characters if they are same. If they are we increment the ref_counter. In this way we calculate the score and print it at the end.

```python
def readFile(filename):
    data = ''
    with open(filename, 'r') as f:
        for x in f.readlines():
            data += ''.join(x.split())
    return data


def is_allowed_specific_char(string):
    allowed_char = set('ACGT')
    validation = set(string)
    if validation.issubset(allowed_char):
        return False
    else:
        return True


def contiguous_compare(cont_seq1, cont_seq2):
    ref_c = 0
    final_c = 0
    c = 0
    for i in range(len(cont_seq1)):
        if cont_seq1[i] == cont_seq2[i]:
            c += 1
            if i < len(cont_seq1) - 1:
                if cont_seq1[i + 1] == cont_seq2[i + 1]:
                    ref_c += 1
        if c != ref_c:
            final_c = c if c > final_c else final_c
            c = 0
            ref_c = 0

    return final_c


def compare_score(comp_seq1, comp_seq2):
    c = 0
    for i in range(len(comp_seq1)):
        if comp_seq1[i] == comp_seq2[i]:
            c += 1
    return c


def get_matches(sequence1, sequence2, maximum_shift, match_method):
    output_seq1 = ''
    output_seq2 = ''
    score = 0
    high_score = 0

    # shift sequence 1
    for i in range(maximum_shift + 1):
        updated_seq1 = sequence1[:-i] if i > 0 else sequence1
        updated_seq2 = sequence2[i:]
        if match_method == 1:
            # compare score
            score = compare_score(updated_seq1, updated_seq2)
        elif match_method == 2:
            # contiguous compare
            score = contiguous_compare(updated_seq1, updated_seq2)

        if score > high_score:
            output_seq1 = 'Sequence 1 --> ' + '_ ' * i + sequence1
            output_seq2 = 'Sequence 2 --> ' + sequence2 + ' _' * i
            high_score = score

    # shift sequence 2
    for i in range(maximum_shift + 1):
        updated_seq1 = sequence1[i:]
        updated_seq2 = sequence2[:-i] if i > 0 else sequence2
        if match_method == 1:
            # compare score
            score = compare_score(updated_seq1, updated_seq2)
        elif match_method == 2:
            # contiguous compare
            score = contiguous_compare(updated_seq1, updated_seq2)

        if score > high_score:
            output_seq1 = 'Sequence 1 --> ' + ' '.join(sequence1) + ' _' * i
            output_seq2 = 'Sequence 2 --> ' + '_ ' * i + ' '.join(sequence2)
            high_score = score
    print('Maximum score is: ' + str(high_score))
    print(output_seq1)
    print(output_seq2)


if __name__ == "__main__":
    try:
        print('\n---------------------------------------------------------------------------------\n')
        filename1 = input('Enter filename for sequence 1: ')
        filename2 = input('Enter filename for sequence 2: ')
        max_shift = int(input('Enter maximum shift: '))
        method = int(input('Enter Method: \n 1. Calculate score \n 2. Maximum Contiguous Chain \n Any other number '
                           'would exit the code.'))

        if method == 1 or method == 2:
            # Read files
            seq1 = readFile(filename1)
            seq2 = readFile(filename2)

            # check for file data length
            if len(seq1) != len(seq2):
                print('Length of sequence is not equal so it cannot be compared.')
                exit()

            if max_shift < 1 or max_shift > (len(seq1)-1):
                print('Max_shift out of range.')
                exit()

            # if the string has the characters it returns false and if not then it returns true
            if is_allowed_specific_char(seq1):
                print('File 1 has other characters except A,C,G,T.')
                exit()

            if is_allowed_specific_char(seq2):
                print('File 2 has other characters except A,C,G,T.')
                exit()

            print('\n---------------------------------------------------------------------------------\n')
            # get our matches
            get_matches(seq1, seq2, max_shift, method)

        else:
            print('Invalid method.')
            exit()
    except FileNotFoundError:
        print('File not found.')
    except ValueError:
        print('File names cannot be empty.')

```

```
seq1.txt file has:
ACTGATCAC

seq2.txt file has:
TTAGCTCGA
```

```
OUTPUT 1: Compare for score
C:\Users\sj779\Pycharm\INF502\venv\Scripts\python.exe C:/Users/sj779/Pycharm/INF502/PA1.py

---------------------------------------------------------------------------------

Enter filename for sequence 1: seq1.txt
Enter filename for sequence 2: seq2.txt
Enter maximum shift: 3
Enter Method: 
 1. Calculate score 
 2. Maximum Contiguous Chain 
 Any other number would exit the code.1

---------------------------------------------------------------------------------

Maximum score is: 4
Sequence 1 --> A C T G A T C A C _ _
Sequence 2 --> _ _ T T A G C T C G A

Process finished with exit code 0
```

```
OUTPUT 2: Contiguous Chain
C:\Users\sj779\Pycharm\INF502\venv\Scripts\python.exe C:/Users/sj779/Pycharm/INF502/PA1.py

---------------------------------------------------------------------------------

Enter filename for sequence 1: seq1.txt
Enter filename for sequence 2: seq2.txt
Enter maximum shift: 3
Enter Method: 
 1. Calculate score 
 2. Maximum Contiguous Chain 
 Any other number would exit the code.2

---------------------------------------------------------------------------------

Maximum score is: 2
Sequence 1 --> ACTGATCAC
Sequence 2 --> TTAGCTCGA

Process finished with exit code 0

```


HURDLES:
Following are the hurdles I faces:
1. While validating the data I had to compare if the data in the file has characters A,G,C,T. I found a lot of ways but could'nt understand the correct regex to compare. I tried packages like 're' and 'sets' but later I found a way to do it with 'set' only.
2. While coding for contiguous, I was confused on how to keep a track of scores and after trying alot I decided to keep multiple counters and keep a check on them. Working that out with hand first actually helped alot and I could complete my code successfully.
3. There were times were I could not keep a track of variables and later I had to write and keep how and when I would be using variables to get an easy outcome from the code.
