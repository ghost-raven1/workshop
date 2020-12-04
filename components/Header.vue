<template>
  <client-only>
    <nav class="uk-navbar-container" uk-sticky="top: 100" uk-navbar>
      <div class="uk-navbar-left">
        <button
          class="uk-button uk-button-default uk-margin-small-right uk-margin-small-left uk-border-rounded uk-visible@s"
          type="button"
          uk-toggle="target: #offcanvas-slide"
        >
          <span uk-icon="icon: menu"></span> Меню
        </button>

        <div id="offcanvas-slide" uk-offcanvas="overlay: true">
          <div class="uk-offcanvas-bar">
            <button class="uk-offcanvas-close" type="button" uk-close></button>

            <ul class="uk-nav uk-nav-default">
              <li class="uk-nav-header">Меню</li>
              <li>
                <a href="/"
                  ><span
                    class="uk-margin-small-right"
                    uk-icon="icon: home"
                  ></span>
                  Каталог</a
                >
              </li>
              <li>
                <a href="/projects"
                  ><span
                    class="uk-margin-small-right"
                    uk-icon="icon: table"
                  ></span>
                  Проекты</a
                >
              </li>
              <li class="uk-nav-divider"></li>
              <li>
                <a href="/"
                  ><span
                    class="uk-margin-small-right"
                    uk-icon="icon: table"
                  ></span>
                  Блог [В разработке]</a
                >
              </li>
            </ul>
          </div>
        </div>

        <ul class="uk-navbar-nav">
          <li class="uk-active">
            <router-link tag="a" class="navbar-brand" to="/" exact
              >Портфолио</router-link
            >
          </li>
        </ul>
      </div>
    </nav>
  </client-only>
</template>

<script>
export default {
  components: {},
  computed: {},
  methods: {}
};
</script>
