# JavaScript bCrypt implementation

Very much based on an existing implementation:
<https://code.google.com/p/javascript-bcrypt/>

Modified to remove dependency on Clipperz and MochiKit, which were only used for
generating a random salt, and logging, respectively.  Possibly this means the
salt is a bit less random, but since the salt is visible in the hash anyway,
this shouldn't be a problem.

Also tidied up code a bit, although there's still work to be done here.

Example usage:

    var pw = "correct horse battery staple";
    var bcrypt = new bCrypt();
    bcrypt.hashpw(pw, bcrypt.gensalt(12), function (hash) {
        console.log("Hash of", pw, "is", hash);
        // Hash of "correct horse battery staple" is
        // "$2a$12$lQbRE0eS17o9PV8LXR22SepbsIk3.4O2bRgi2d.3e4.H8O45TzTqe"
    });
