package design_patterns;

//eager (final keyword --> it prevent the reinitialize the variable named instance and private constructor --> prevent the creation of instance outside the class)

public class Logger {
	
	private static final Logger instance = new Logger();
	
	private Logger() {}
	
	public static Logger getInstance() {
		return instance;
	}
}


//lazy (Synchronized keyword --> make it safe in multi-threaded app)

public class Logger{
	
	private static Logger instance;
	
	private Logger() {};
	
	public static synchronized getInstance() {
		if(instance == null) {
			instance = new Logger();     // create once
		}
		return instance;
	}
}


class Test{
	Logger l = new Logger();   // it show as error because constructor is private.
	l.getInstance();
}
