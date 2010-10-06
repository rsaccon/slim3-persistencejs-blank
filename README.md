Serverside sync (in Java / on appengine) for persistencejs - blank project
==========================================================================

This is a blank project, containing only all the necessary boilerplate stuff, for getting you started easily ...

Requirements: 
-------------
* eclipse with appengine plugin

How to:
-------
* Import this project into eclipse, disconnect it from git and rename it.
* Use the gen-persistencejs-sync task to create synced model and associated controller.
* Add fields to models as usual, use Sync annotation to mark fields for sync
* After generating setter/getter for new fields, insert at the setter body a meta function (which checks/sets a dirty field), see example below:

<code>
	public class MyModel implements Serializable {
		
		// ... [cutted out]
		
		@Sync
    	private String foo;
		
		// ... [cutted out]
		
		public void setFoo(String foo) {
        	MyModelMeta.get().syncFoo(this, foo);  // <<< ADD THIS !!!
        	this.foo = foo;
    	}
    }
</code>

Links:
------
* [persistencejs](http://github.com/zef/persistencejs)
* [slim3](http://code.google.com/p/slim3)
* [slim3 persistencejs demo (testsuite)](http://github.com/rsaccon/Slim3PersistenceSync)
