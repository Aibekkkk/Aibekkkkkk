# Aibekkkkkk
#11:11
from PyQt5.QtCore import Qt
from PyQt5.QtWidgets import QApplication, QWidget, QPushButton, QLabel, QVBoxLayout, QHBoxLayout, QTextEdit, QListWidget,QLineEdit
import json

app = QApplication([])
main_win = QWidget()
main_win.setWindowTitle('moral_help_in_any_situation_for_you')


but_ADD = QPushButton('ADD')
but_SAVE = QPushButton('SAVE_THIS_SHIT')
but_DEL = QPushButton('DELETE THIS GOVNO')

p1 = QPushButton('GOOD WORDS')
p3 = QLabel('You are good at this)')
p5 =QLabel('You are the best))))')

main_layout = QHBoxLayout()
line1 = QVBoxLayout()
line3 = QHBoxLayout()

line1.addWidget(p1 , alignment = Qt.AlignCenter)
line1.addWidget(p3, alignment = Qt.AlignCenter)
line1.addWidget(p5, alignment = Qt.AlignCenter)

line3.addWidget(but_ADD , alignment = Qt.AlignRight)
line3.addWidget(but_DEL , alignment = Qt.AlignRight)
line3.addWidget(but_SAVE , alignment = Qt.AlignRight)

main_layout.addLayout(line1)
main_layout.addLayout(line3)

main_win.setLayout(main_layout)



words_inf = QTextEdit()
line1.addWidget(words_inf)
line1.addLayout(line3)

words_list = QListWidget()
main_layout.addWidget(words_list)
main_layout.addLayout(line1)


words_eddit = QLineEdit()
words_eddit.setPlaceholderText('ВВедите слова:')
line1.addWidget(words_eddit)

with open('words.json', 'r') as file:
    words = json.load(file)
    for word in words:
        words_list.addItem(word)

def add_word():
    word = words_edit.text()
    with open('words.json', 'r') as file:
        words = json.load(file)
    words[word] = ''
    with open('words.json', 'w') as file:
        words = json.dump(words, file)
    words_edit.clear()
    words_list.addItem(word)


def edit_word():
    word = ''
    if words_list.selectedItems()[0].text:
        word = words_list.selectedItem()[0].text()
    with open('words.json', 'r') as file:
        words = json.load(file)
    words[word] = words_info.toPlainText
    with open('words.json', 'w') as file:
        words = json.dump(words, file)
    words_edit.clear()
    words_list.addItem(word)


def del_word():
    word = ''
    if words_list.selectedItems()[0].text:
        word = words_list.selectedItem()[0].text()
    with open('words.json', 'r') as file:
        words = json.load(file)
    words[word] = words_info.toPlainText
    with open('words.json', 'w') as file:
        words = json.dump(words, file)
    words_edit.clear()
    words_list.addItem(word)





main_win.show()
app.exec_()
