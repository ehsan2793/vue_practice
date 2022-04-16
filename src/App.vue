<template>
  <section>
    <header><h1>My friends</h1></header>
    <New-friend @add-friend="addNewFriend" />
    <ul>
      <Friend-contact
        v-for="friend in friends"
        :id="friend.id"
        :key="friend.id"
        :name="friend.name"
        :phone="friend.phone"
        :email="friend.email"
        :is-favorite="friend.isFavorited"
        @toggle-favorite="toggleFavorite"
        @delete-friend="deleteFriend"
      />
    </ul>
  </section>
</template>

<script>
export default {
  data() {
    return {
      friends: [
        {
          id: 1,
          name: 'arsalan',
          phone: '123 2135 123',
          email: 'arsalan.gmail.com',
          isFavorited: true,
        },
        {
          id: 2,
          name: 'mom',
          phone: '098 2135 123',
          email: 'mom.gmail.com',
          isFavorited: false,
        },
        {
          id: 3,
          name: 'baba',
          phone: '556 2135 123',
          email: 'baba.gmail.com',
          isFavorited: false,
        },
      ],
    };
  },

  methods: {
    toggleFavorite(friendId) {
      const foundFriend = this.friends.find((friend) => friend.id === friendId);
      foundFriend.isFavorited = !foundFriend.isFavorited;
    },
    addNewFriend(name, phone, email) {
      const newfriend = {
        id: Math.random() * 1000,
        name,
        phone,
        email,
        isFavorited: false,
      };
      this.friends.push(newfriend);
    },
    deleteFriend(friendId) {
      this.friends = this.friends.filter((item) => item.id !== friendId);
    },
  },
};
</script>

<style>
* {
  box-sizing: border-box;
}
html {
  font-family: 'Jost', sans-serif;
}
body {
  margin: 0;
}
header {
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  margin: 3rem auto;
  border-radius: 10px;
  padding: 1rem;
  background: #50004d;
  color: #fff;
  text-align: center;
  widows: 90%;
  max-width: 40rem;
}

#app ul {
  margin: 0;
  padding: 0;
  list-style: none;
}
#app li,
#app form {
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  margin: 1rem auto;
  border-radius: 10px;
  padding: 1rem;
  text-align: center;
  width: 90%;
  max-width: 40rem;
}
#app h2 {
  font-size: 2rem;
  border-bottom: 4px solid #ccc;
  margin: 0 0 1rem 0;
  color: #58004d;
}

#app button {
  font: inherit;
  cursor: pointer;
  border: 1px solid #ff0077;
  background: #ff0077;
  color: #fff;
  padding: 0.05rem 1rem;
  box-shadow: 1px 1px 2px rgba(0, 0, 0, 0.26);
  border-radius: 10px;
}

#app button:hover,
#app button:active {
  background: #ec3169;
  border-color: #ec3169;
  box-shadow: 2px 5px 10px rgba(0, 0, 0, 0.56);
}

#app input {
  font: inherit;
  padding: 0.15rem;
}
#app label {
  font-weight: bold;
  margin-right: 1rem;
  width: 7rem;
  display: inline-block;
}
#app form div {
  margin: 1rem 0;
}
</style>
