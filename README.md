# hello



    myemail = findViewById(R.id.email)
        mypassword = findViewById(R.id.pass)
        myconfpassword = findViewById(R.id.confirmpass)
        signup = findViewById(R.id.btnSign)
        mylogin = findViewById(R.id.text)
        auth = Firebase.auth


        mylogin.setOnClickListener {
            val intent = Intent(this, LoginActivity::class.java)
            startActivity(intent)
            finish()
        }

        signup.setOnClickListener {
            SignUpUser()
        }
    }

    private fun SignUpUser(){
        val email=myemail.text.toString()
        val pass=mypassword.text.toString()
        val confirmpass=myconfpassword.text.toString()
        if (email.isBlank() || confirmpass.isBlank()){
            Toast.makeText(this,"Please Email and password cant be blank",Toast.LENGTH_LONG).show()
            return

        } else if (pass != confirmpass){
            Toast.makeText(this,"Password do not match",Toast.LENGTH_LONG).show()
        }

        auth.createUserWithEmailAndPassword(email,pass).addOnCompleteListener(this)
         if (it.isSuccessful){
             Toast.makeText(this,"Signed up successfully",Toast.LENGTH_LONG).show()

         }else{
             Toast.makeText(this,"Failed to create",Toast.LENGTH_LONG).show()
         }


    }
}
