<template>
  <div class="person">
    <div class="person__info-main">
      <div class="person__photo">
        <img :src="person.picture" alt="photo" />
      </div>
      <div class="person__info-name">
        <b>{{ person.name }} ({{ person.age }})</b>
      </div>
    </div>

    <div class="person__info">
      <div class="person__info-email"><MailSVG />{{ person.email }}</div>
      <div class="person__info-registered">
        Дата регистрации: {{ formatedDate }}
      </div>
      <div class="person__info-about">О себе: {{ person.about }}</div>
    </div>
  </div>
</template>

<script>
import { format, parseISO } from "date-fns";
import MailSVG from "@/assets/images/email.svg";

export default {
  props: {
    person: {
      type: Object,
      default: null,
    },
  },
  components: {
    MailSVG,
  },
  computed: {
    formatedDate() {
      return format(parseISO(this.person.registered), "dd.mm.yyyy");
    },
  },
};
</script>

<style scoped>
.person {
  display: flex;
  flex-direction: column;
}

.person__info-main {
  width: max-content;
  display: flex;
  justify-content: space-between;
  gap: 10px;
}

.person__photo img {
  height: 100px;
  width: 100px;
  border-radius: 6%;
  grid-area: photo;
}

.person__info {
  display: grid;
  grid-gap: 8px;
  grid-area: info;
}

.person__info-name {
  display: flex;
  justify-content: center;
  margin-bottom: 10px;
}
.person__info-email {
  display: flex;
  align-items: center;
  margin-bottom: 10px;
  gap: 5px;
}
</style>
