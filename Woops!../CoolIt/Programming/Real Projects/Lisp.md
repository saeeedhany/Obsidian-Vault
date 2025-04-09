My own *lisp* language with *C*.

Here i'll put some of my highlight of my trip to building this hole shit :b 

#### **Things i want to search about**
- *Puts* and *fputs* and *fgets*.
- *stdout* and *stdin* functions and how they works.


### Labels
**Compilation :**
We use *Gnome C Compiler (GCC)* for the compilation process.

**The *C* Preprocessor :**
For such a small projects it might be okay that we have to program differently depending on what operating system we are using, but if i want to send my source code to a friend on different operating system to give me a hand with the programming, it is going to cause a problem. In an ideal world i'd with for my source code to be able to compile on matter where, or on what computer, it is being compiled. This is a general problem in C, and it is called *portability*. there is not always an easy or correct solution.

**Languages** *What is a programming language ?*..
- **Chomsky hierarchy** _research_
	some description..
- **Parser Combinators** *mpc* :
	this *parser combinator library* is written by the author of the book,
	it's a library that allows me to build programs that understand and process particular languages. *but the cool thing about using a parser combinator library is that it lets you build parsers  easily, just by specifying the grammar... sort of.*
	- after knowing the rules..
		We can starting by trying to define *Adjective* and *Noun*. To do this we create two new parsers, represented by the type *mpc_parser_t*, and we store them in the variables *Adjective* and *Noun*. We use the function *mpc_or* to create a parser where one of several options should be used, and the function *mpc_sys* to wrap our initial string.
		**Like this ..**
		```C
		mpc_parser_t Adjective = mpc_or(4, 
			mpc_sys("wow"), mpc_sys("many"),
			mpc_sys("so"), mpc_sys("such")
		);
		mpc_parser_t Noun = mpc_or(5,
			mpc_sys("lisp"), mpc_sys("language"),
			mpc_sys("book"), mpc_sys("build"),
			mpc_sys("c")
		);
		```
		**So how can i access them?**
		To define *Phrase (statement)* we can reference our existing parsers. We need to use the function *mpc_and*, that specifies one thing is required then another. As input we pass it *Adjective* and *Noun*, our previously defined parsers, this function also takes the arguments *mpcf_strfold* and *free*, which say how to join or delete the results of these parsers.
		```C
		mpc_parser_t* Phrase = mpc_and(2, mpcf_strfold, Phrase); //ignore
		```

		And to define *Doge* we must specify that *zero* or more of some parsers is required.
		For this we need to use the function *mpc_many*. As before, this function requires the special variable *mpcf_strfold* to say how the result are joined together.
		```C
		mpc_prser_t* Doge = mpc_many(mpcf_strfold, Phrase)
		```
		By creating a parser that looks for *zero* or *more occurrences* of another parser an interesting thing has happened, Our Doge parser accepts inputs of any length.
		This means its language is infinite. Here are just some example of possible strings Doge could accept. Just as we  discovered in the first section of this chapter we have used a finite number of re-write rules to create an infinite language.
		
-  
