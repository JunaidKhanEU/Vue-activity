<template>
  <div id="app">
    <nav class="navbar is-white topNav">
      <div class="container">
        <div class="navbar-brand">
          <h1>Activity Planner</h1>
        </div>
      </div>
    </nav>
    <nav class="navbar is-white">
      <div class="container">
        <div class="navbar-menu">
          <div class="navbar-start">
            <a class="navbar-item is-active" href="#">Newest</a>
            <a class="navbar-item" href="#">In Progress</a>
            <a class="navbar-item" href="#">Finished</a>
          </div>
        </div>
      </div>
    </nav>

    <section class="container">
      <div class="columns">
        <div class="column is-3">
          <a
            class="button is-primary is-block is-alt is-large"
            href="#"
            @click="isFormDisplayed = !isFormDisplayed"
            v-if="isFormDisplayed == false"
          >New Activity</a>
          <div class="create-form" v-if="isFormDisplayed">
            <h2>Create Activity</h2>
            <form>
              <div class="field">
                <label class="label">Title</label>
                <div class="control">
                  <input
                    class="input"
                    type="text"
                    placeholder="new activity"
                    v-model="newActivity.title"
                  >
                </div>
              </div>
              <div class="field">
                <label class="label">Notes</label>
                <div class="control">
                  <textarea
                    class="textarea"
                    placeholder="write some notes here"
                    v-model="newActivity.notes"
                  ></textarea>
                </div>
              </div>
              <div class="field is-grouped">
                <div class="control">
                  <button class="button is-link" @click="createActivity">Create Activity</button>
                  <button class="button is-text" @click="isFormDisplayed = !isFormDisplayed">cancel</button>
                </div>
              </div>
            </form>
          </div>
        </div>
        <div class="column is-9">
          <div class="box content">
            <ActivityItem v-for="(activity,i) in activities" :activity="activity" :key="i"></ActivityItem>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
import ActivityItem from "./components/ActivityItem";
export default {
  name: "app",
  components: {
    ActivityItem
  },
  data() {
    return {
      isFormDisplayed: false,
      message: "hello Vue",
      titleMessage: "Title Message Vue!!!!!",
      isTextDisplayed: true,
      newActivity: {
        title: "",
        notes: ""
      },
      user: {
        name: "Filip Jerga",
        id: "-Aj34jknvncx98812"
      },
      activities: {
        "1546968934": {
          title: "Learn Vue.js",
          notes: "I started today and it was not good.",
          progress: 0,
          category: "1546969049",
          createdAt: 1546969144391,
          updatedAt: 1546969144391
        },
        "1546969212": {
          title: "Read Witcher Books",
          notes: "These books are super nice",
          progress: 0,
          category: "1546969049",
          createdAt: 1546969144391,
          updatedAt: 1546969144391
        }
      },
      categories: {
        "1546969049": {
          text: "books"
        },
        "1546969225": {
          text: "movies"
        }
      }
    };
  },
  methods: {
    toggleDisplay() {
      this.isTextDisplayed = !this.isTextDisplayed;
    },
    createActivity() {
      console.log(this.newActivity);
    }
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}

html,
body {
  font-family: "Open Sans", serif;
  background: #f2f6fa;
}

footer {
  background-color: #f2f6fa !important;
}

.topNav {
  border-top: 5px solid #3498db;
}

.topNav .container {
  border-bottom: 1px solid #e6eaee;
}

.container .columns {
  margin: 3rem 0;
}

.navbar-menu .navbar-item {
  padding: 0 2rem;
}

aside.menu {
  padding-top: 3rem;
}

aside.menu .menu-list {
  line-height: 1.5;
}

aside.menu .menu-label {
  padding-left: 10px;
  font-weight: 700;
}

.button.is-primary.is-alt {
  background: #00c6ff;
  background: -webkit-linear-gradient(to bottom, #0072ff, #00c6ff);
  background: linear-gradient(to bottom, #0072ff, #00c6ff);
  font-weight: 700;
  font-size: 14px;
  height: 3rem;
  line-height: 2.8;
}

.media-left img {
  border-radius: 50%;
}

.media-content p {
  font-size: 14px;
  line-height: 2.3;
  font-weight: 700;
  color: #8f99a3;
}

article.post {
  margin: 1rem;
  padding-bottom: 1rem;
  border-bottom: 1px solid #e6eaee;
}

article.post:last-child {
  padding-bottom: 0;
  border-bottom: none;
}

.menu-list li {
  padding: 5px;
}

.navbar-brand > h1 {
  font-size: 31px;
  padding: 20px;
}
</style>
