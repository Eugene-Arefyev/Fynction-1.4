# Fynction-1.4
documents = [
        {"type": "passport", "number": "2207 876234", "name": "Василий Гупкин"},
        {"type": "invoice", "number": "11-2", "name": "Геннадий Покемонов"},
        {"type": "insurance", "number": "10006", "name": "Аристарх Павлов"}
      ]

directories = {
        '1': ['2207 876234', '11-2'],
        '2': ['10006'],
        '3': []
      }
 Необходимо реализовать пользовательские команды, которые будут выполнять следующие функции:   
# p – people – команда, которая спросит номер документа и выведет имя человека, которому он принадлежит;
# l – list – команда, которая выведет список всех документов в формате passport "2207 876234" "Василий Гупкин";
# s – shelf – команда, которая спросит номер документа и выведет номер полки, на которой он находится;
# a – add – команда, которая добавит новый документ в каталог и в перечень полок, спросив его номер, тип, имя владельца и номер полки, на котором он будет храниться.


def people():
	print('Введите № документа: ')
	number_doc = input()
	for document in documents:
		if document['number'] == number_doc:
			print(document['name'])

def li_st():
	for document in documents:
		print('{} {} {}'.format(document['type'], document['number'], document['name']))


def shelf():
	print('Введите № ')
	num_doc = input()
	for key_directories in directories:
		for values_directories in directories[key_directories]:
			if (num_doc == values_directories):
				print('Полка №:', key_directories)
				

def add_document():
	add_doc = input('Type (passport, invoice, insurance):')
	add_number = input('number:')
	add_name = input('name:')
	information = {'type': add_doc, 'number': add_number, 'name': add_name}
	add_key = input('directory:')
	directories[add_key].append(add_number)
	documents.append(information)


def new_documents_list():
  for document in documents:
    print('{} {} {}'.format(document['type'], document ['number'], document ['name']))


def main():
  print ("Что вы хотите сделать? \n 1. Узнать ФИО человека по номеру документа? \n 2. Вывести список всех документов и информацию о них? \n 3.Узнать номер полки, на которой храниться документ? \n 4. Добавить новые документ для хранения? \n Введите номер функции для ее исполнения:")
  user_input = input()
  if user_input == '1':
    people()
  elif user_input == '2':
    li_st()
  elif user_input == '3':
    shelf()
  elif user_input == '4':
    add_document()
    new_documents_list() 
  else:
    print ("Вы не верно ввели номер функции")
    
while True:
  main()
