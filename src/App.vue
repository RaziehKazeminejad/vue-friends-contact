<template>
  <header>
    <h1>My Friend</h1>
  </header>
  <new-friend @add-contact="addContact"></new-friend>
  <friend-contact
    v-for="friend in friends"
    :key="friend.id"
    :id="friend.id"
    :name="friend.name"
    :phone-number="friend.phone"
    :email-address="friend.email"
    :is-favorite="friend.isFavorite"
    @toggle-favorite="toggleFavoriteStatus"
    @delete="deleteContact"
  />
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      friends: [
        {
          id: "Mary",
          name: "Mary Smith",
          email: "Mary@gmail.com",
          phone: "0912 345 6789",
          isFavorite: true,
        },
        {
          id: "Sarah",
          name: "Sarah Doe",
          email: "sara@gmail.com",
          phone: "0913 345 6789",
          isFavorite: false,
        },
      ],
    };
  },
  methods: {
    toggleFavoriteStatus(friendId) {
      const identifiedFriend = this.friends.find(
        (friend) => friend.id === friendId
      );
      identifiedFriend.isFavorite = !identifiedFriend.isFavorite;
    },
    addContact(name, phone, email) {
      const newFriendContact = {
        id: new Date().toISOString,
        name: name,
        email: email,
        phone: phone,
        isFavorite: false,
      };
      this.friends.push(newFriendContact);
    },
    deleteContact(friendId) {
      this.friends = this.friends.filter((friend) => friend.id !== friendId);
    },
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Fredoka+One&display=swap");
@import url("https://fonts.googleapis.com/css2?family=Noto+Sans:wght@400;700&display=swap");

:root {
  --blue-1: #273974;
  --yellow-1: #f18805;
  --yellow-2: #f0a202;
  --gray-1: #455959;
  --gray-2: #a9c0c0;
  --white-1: #e0fbfc;
  --font-primary: "Noto Sans", sans-serif;
  --font-display: "Fredoka One", cursive;
}
* {
  box-sizing: border-box;
}
html {
  font-family: var(--font-primary);
}
body {
  margin: 0;
}
header {
  box-shadow: 0 2px 8px var(--gray-1);
  margin: 1rem auto;
  border-radius: 10px;
  padding: 5px;
  background-color: var(--blue-1);
  color: var(--white-1);
  text-align: center;
  width: 90%;
  max-width: 40rem;
}
#app ul {
  margin: 0;
  padding: 0;
  list-style: none;
}
#app li,
#app form {
  list-style: none;
  box-shadow: 0 2px 8px var(--gray-1);
  margin: 1rem auto;
  border-radius: 10px;
  padding: 1rem;
  text-align: center;
  width: 90%;
  max-width: 40rem;
}
#app h1 {
  font-family: var(--font-display);
}
#app h2 {
  font-family: var(--font-primary);
  font-size: 1.5rem;
  color: var(--blue-1);
  margin: 0 0 1rem 0;
}
#app button {
  font: inherit;
  cursor: pointer;
  border: none;
  border-radius: 5px;
  background-color: var(--yellow-1);
  color: white;
  padding: 0.5rem 1rem;
  margin: 1rem;
}
#app button:hover,
#app button:active {
  background-color: var(--yellow-2);
  border-color: var(--yellow-2);
  box-shadow: 1px 1px 4px var(--gray-1);
}
#app input {
  font: inherit;
  padding: 8px;
  border: 1px solid var(--gray-2);
  border-radius: 5px;
  width: 20rem;
  max-width: 40rem;
}
#app label {
  font-weight: bold;
  color: var(--blue-1);
  margin-right: 1rem;
  width: 7rem;
  display: inline-block;
}
#app form div {
  margin: 1rem 0;
}
</style>
