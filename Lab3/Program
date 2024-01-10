using System;
using System.Collections.Generic;
using System.Linq;
using System.Windows;

namespace Lab3
{
    public class Program
    {
        public static void Main(string[] args)
        {
            Library library = new Library();
            IEnumerable<Book> foundBooks;
            IEnumerable<Library.BookSearchResult> foundBooksResult;
            while (true)
            {
                Console.WriteLine("Книжный каталог. Выберете операцию:");
                Console.WriteLine("1 - добавление книги в каталог");
                Console.WriteLine("2 - выбрать книгу");
                Console.WriteLine("3 - сохранить в файл");
                Console.WriteLine("4 - загрузить из файла");
                Console.WriteLine("5 - выход");
                string choose;
                string operation = Console.ReadLine();
                switch (operation)
                {
                    case "1":
                        Console.WriteLine("Введите название книги:");
                        string title = Console.ReadLine();
                        Console.WriteLine("Введите автора книги:");
                        string author = Console.ReadLine();
                        Console.WriteLine("Введите жанр книги:");
                        string genre = Console.ReadLine();
                        Console.WriteLine("Введите ISBN книги:");
                        string isbn = Console.ReadLine();
                        Console.WriteLine("Введите аннотацию:");
                        string annotation = Console.ReadLine();
                        Console.WriteLine("Введите дату публикации книги (в формате ГГГГ-ММ-ДД):");
                        bool isValidDate = false;
                        DateTime publicationDate;
                        string inputDate = Console.ReadLine();
                        isValidDate = DateTime.TryParse(inputDate, out publicationDate);
                        while (!isValidDate)
                        {
                            Console.WriteLine("Неверный формат даты. Пожалуйста, введите дату в правильном формате.");
                            inputDate = Console.ReadLine();
                            isValidDate = DateTime.TryParse(inputDate, out publicationDate);
                        }
                        Book newBook = new Book(title, author, genre, publicationDate, isbn, annotation);
                        library.Add(newBook);
                        Console.WriteLine("Книга успешно добавлена в каталог.");
                        break;
                    case "2":
                        Console.WriteLine("Выберете по чему производить поиск:");
                        Console.WriteLine("1 - Названию или его фрагменту");
                        Console.WriteLine("2 - имени автора");
                        Console.WriteLine("3 - ключевым словам");
                        choose = Console.ReadLine();
                        switch (choose)
                        {
                            case "1":
                                Console.WriteLine("Введите название книги или его часть:");
                                string searchTitle = Console.ReadLine();
                                Predicate<Book> titlePredicate = book => book.Title.Contains(searchTitle);
                                foundBooks = library.Search(titlePredicate);
                                if (foundBooks.Any())
                                {
                                    Console.WriteLine("Книги найдены!");
                                    foreach (var book in foundBooks)
                                    {
                                        Console.WriteLine(book.ToString());
                                    }
                                }
                                else
                                {
                                    Console.WriteLine("Книга не найдена.");
                                }
                                break;
                            case "2":
                                Console.WriteLine("Введите имя автора:");
                                string searchAuthor = Console.ReadLine();
                                Predicate<Book> authorPredicate = book => book.Author.Contains(searchAuthor);
                                foundBooks = library.Search(authorPredicate);
                                if (foundBooks.Any())
                                {
                                    Console.WriteLine("Книги найдены!");
                                    foreach (var book in foundBooks)
                                    {
                                        Console.WriteLine(book.ToString());
                                    }
                                }
                                else
                                {
                                    Console.WriteLine("Книга не найдена.");
                                }
                                break;
                            case "3":
                                Console.WriteLine("Введите ключевые слова:");
                                string[] searchKeyWords = Console.ReadLine().Split();
                                foundBooksResult = library.Search(searchKeyWords);
                                if (foundBooksResult.Any())
                                {
                                    Console.WriteLine("Книги найдены!");
                                    foreach (var book in foundBooksResult)
                                    {
                                        Console.WriteLine(book.ToString());
                                    }
                                }
                                else
                                {
                                    Console.WriteLine("Книга не найдена.");
                                }
                                break;
                            default:
                                Console.WriteLine("Неверная операция. Пожалуйста, выберите 1, 2 или 3.");
                                break;
                        }
                        break;
                    case "3":
                        Console.WriteLine("Выберете формат сохранения:");
                        Console.WriteLine("1 - Сохранить в файл формата JSON");
                        Console.WriteLine("2 - Сохранить в файл формата XML");
                        Console.WriteLine("3 - Сохранить в файл формата SQLite");
                        choose = Console.ReadLine();
                        switch (choose)
                        {
                            case "1":
                                if (library.SaveToJSON())
                                {
                                    Console.WriteLine("Успешно сохранили");
                                }
                                break;
                            case "2":
                                if (library.SaveToXML())
                                {
                                    Console.WriteLine("Успешно сохранили");
                                }
                                break;
                            case "3":
                                if (library.SaveToSQLite())
                                {
                                    Console.WriteLine("Успешно сохранили");
                                }
                                break;
                            default:
                                Console.WriteLine("Неверная операция. Пожалуйста, выберите 1, 2 или 3.");
                                break;
                        }
                        break;
                    case "4":
                        Console.WriteLine("Выберете формат загрузки:");
                        Console.WriteLine("1 - Загрузить из файла формата JSON");
                        Console.WriteLine("2 - Загрузить из файла формата XML");
                        Console.WriteLine("3 - Загрузить из файла формата SQLite");
                        choose = Console.ReadLine();
                        switch (choose)
                        {
                            case "1":
                                if (library.LoadFromJSON())
                                {
                                    Console.WriteLine("Успешно загрузили");
                                }
                                break;
                            case "2":
                                if (library.LoadFromXML())
                                {
                                    Console.WriteLine("Успешно загрузили");
                                }
                                break;
                            case "3":
                                if (library.LoadFromSQLite())
                                {
                                    Console.WriteLine("Успешно загрузили");
                                }
                                break;
                            default:
                                Console.WriteLine("Неверная операция. Пожалуйста, выберите 1, 2 или 3.");
                                break;
                        }
                        break;
                    case "5":
                        Environment.Exit(0);
                        break;
                    default:
                        Console.WriteLine("Неверная операция. Пожалуйста, выберите 1, 2, 3, 4, 5");
                        break;
                }
            }
        }
    }
}
