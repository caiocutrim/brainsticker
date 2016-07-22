<template>

</template>


<script>

  // Initialize Firebase
  var config = {
    apiKey: "AIzaSyBlGaFCzgYZ7EfD2V_P99kYx5YJnEMPEjs",
    authDomain: "brainsticker-95fb9.firebaseapp.com",
    databaseURL: "https://brainsticker-95fb9.firebaseio.com",
    storageBucket: "",
  };

  firebase.initializeApp(config);

let provider,
providers = {
	github: new firebase.auth.GithubAuthProvider(),
	facebook: new firebase.auth.FacebookAuthProvider()
}

function Provider(choosenProvider) {
	providers[choosenProvider]
}


const login = () => {
	firebase.auth().signInWithPopup(provider)
		.then(function(result) {
			// This gives you a GitHub Access Token. You can use it to access the GitHub API.
			console.log(result.user)
			console.log(result.credential.accessToken)
			var token = result.credential.accessToken;
			// The signed-in user info.
			var user = result.user;
			// ...
		})
		.catch(function(error) {
			// Handle Errors here.
			var errorCode = error.code;
			var errorMessage = error.message;
			// The email of the user's account used.
			var email = error.email;
			// The firebase.auth.AuthCredential type that was used.
			var credential = error.credential;
		// ...
		});
}

new Vue({
  el: '#login',
  data: {
    provider: () => {
      return console.log('oi')
    }
  }

});
</script>

<style lang="css">
</style>
