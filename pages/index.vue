<template>
  <div>
    <form class="search_input">
      <span uk-search-icon></span>
      <input
        class="uk-search-input"
        v-model="query"
        type="search"
        placeholder="Поиск по проектам..."
      />
    </form>

    <div
      class="uk-card uk-card-default uk-grid-collapse uk-child-width-1-2@m uk-margin"
      v-for="project in filteredList"
      v-bind:key="project"
      uk-grid
    >
      <div class="uk-card-media-left uk-cover-container">
        <img
          :src="'http://localhost:1337' + project.image.url"
          alt=""
          uk-cover
        />
        <canvas width="600" height="400"></canvas>
      </div>
      <div>
        <div class="uk-card-body">
          <h1 class="uk-card-title">
            {{ project.name }} - {{ project.site_url }}
          </h1>
          <ul uk-accordion>
            <li>
              <a class="uk-accordion-title" href="#">Описание</a>
              <div class="uk-accordion-content">
                <p>
                  {{ project.body }}
                </p>
              </div>
            </li>
          </ul>

          <ul uk-accordion>
            <li>
              <a class="uk-accordion-title" href="#">Стэк технологий</a>
              <div class="uk-accordion-content">
                <ul>
                  <li>Фронтенд: {{ project.CMS_framework_frontend }}</li>
                  <li>Бэкенд: {{ project.CMS_framework_backend }}</li>
                  <li>База данных: {{ project.db }}</li>
                </ul>
              </div>
            </li>
          </ul>

          <a
            :href="'//' + project.site_url"
            target="_blank"
            rel="nofollow"
            class="uk-button uk-button-primary uk-border-rounded"
          >
            Посмотреть проект
          </a>
        </div>
      </div>
    </div>

    <div
      class="uk-container uk-container-center uk-text-center"
      v-if="filteredList.length == 0"
    >
      <img
        src="https://assets-ouch.icons8.com/preview/19/52de2377-696e-4194-8c63-0a81aef60b4f.png"
        height="800"
        width="800"
      />
      <p>Проекты не найдены!</p>
    </div>
  </div>
</template>

<script>
import projectsQuery from "~/apollo/queries/project/projects";

export default {
  data() {
    return {
      projects: [],
      query: ""
    };
  },
  apollo: {
    projects: {
      prefetch: true,
      query: projectsQuery
    }
  },
  computed: {
    filteredList() {
      return this.projects.filter(project => {
        return project.name.toLowerCase().includes(this.query.toLowerCase());
      });
    }
  }
};
</script>
