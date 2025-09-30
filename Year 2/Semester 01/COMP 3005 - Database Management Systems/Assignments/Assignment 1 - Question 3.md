
```
CREATE TABLE Books (
	book_id SERIAL PRIMARY KEY,
	title VARCHAR(255) NOT NULL,
	author_id INT REFERENCES Authors(author_id),
	publisher_id INT REFERENCES Publishers(publisher_id),
	published_date DATE,
	isbn VARCHAR(13) UNIQUE,
	available_copies INTEGER NOT NULL DEFAULT 1
);

CREATE TABLE Members (
	member_id SERIAL PRIMARY KEY,
	first_name VARCHAR(255) NOT NULL,
	last_name VARCHAR(255) NOT NULL,
	email VARCHAR(255) UNIQUE NOT NULL,
	phone VARCHAR(15),
	join_date DATE DEFAULT CURRENT_DATE
);

CREATE TABLE Borrowing (
	borrow_id SERIAL PRIMARY KEY,
	book_id INT REFERENCES Books(book_id),
	member_id INT REFERENCES Members(member_id),
	borrow_date DATE DEFAULT CURRENT_DATE,
	return_date DATE
);

CREATE TABLE Authors (
	author_id SERIAL PRIMARY KEY,
	first_name VARCHAR(255) NOT NULL,
	last_name VARCHAR(255) NOT NULL,
	bio TEXT
);

CREATE TABLE Publishers (
	publisher_id SERIAL PRIMARY KEY,
	publisher_name VARCHAR(255) NOT NULL,
	address VARCHAR(255)
);
```
