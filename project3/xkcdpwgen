#!/usr/bin/env python3
import argparse
import random
import string
import os

WORDS_PATH = "words.txt"
SYMBOLS = "~!@#$%^&*.:;"

def get_random_words(n):
    with open(WORDS_PATH, 'r') as f:
        words = [word.strip() for word in f]
    return random.sample(words, n)

def capitalize_random(words, n):
    indices = random.sample(range(len(words)), min(n, len(words)))
    for i in indices:
        words[i] = words[i].capitalize()
    return words

def insert_random_chars(words, n, chars):
    for _ in range(n):
        word_index = random.randint(0, len(words) - 1)
        char_index = random.randint(0, len(words[word_index]))
        char = random.choice(chars)
        words[word_index] = words[word_index][:char_index] + char + words[word_index][char_index:]
    return words

def main():
    parser = argparse.ArgumentParser(description='Generate a secure, memorable password using the XKCD method.')
    parser.add_argument('-w', '--words', type=int, default=4, help='include WORDS words in the password (default=4)')
    parser.add_argument('-c', '--caps', type=int, default=0, help='capitalize the first letter of CAPS random words (default=0)')
    parser.add_argument('-n', '--numbers', type=int, default=0, help='insert NUMBERS random numbers in the password (default=0)')
    parser.add_argument('-s', '--symbols', type=int, default=0, help='insert SYMBOLS random symbols in the password (default=0)')
    
    args = parser.parse_args()
    
    words = get_random_words(args.words)
    words = capitalize_random(words, args.caps)
    words = insert_random_chars(words, args.numbers, string.digits)
    words = insert_random_chars(words, args.symbols, SYMBOLS)
    
    print(''.join(words))

if __name__ == "__main__":
    main()


