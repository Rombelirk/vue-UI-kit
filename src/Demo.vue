<template>
  <form @submit="onPressEnter" class="demo">
    <div class="alert-container">
      <toggle :toggled="dangerAlerts" :onToggle="onToggle" />
      <div class="toggle-description">Change alert type to {{dangerAlerts ? 'notice' : 'error'}}</div>
    </div>
    <alert
      :message="alert.text || ''"
      :key="index"
      v-for="(alert, index) in alerts"
      :type="dangerAlerts ? 'danger' : 'notice'"
      :onRemove="onAlertRemove"
      :id="alert.id"
    />
    <text-input
      :onChange="onAlertType"
      :value="currentAlert"
      :placeholder="'Type something cool here... Dont leave empty!'"
      :error="inputError"
    />
    <div class="button-container">
      <base-button :disabled="addingAlertsDisabled" :onClick="addAlert">Add</base-button>
      <div class="add-button-description">
        <span v-if="addingAlertsDisabled">Sorry, can't add more alerts :(</span>
        <span v-else>3 alerts maximum. {{3-this.alerts.length}} left...</span>
      </div>
    </div>
  </form>
</template>

<script>
import Switch from "./components/Switch/Switch";
import Alert from "./components/Alert/Alert";
import Input from "./components/Input/Input";
import Button from "./components/Button/Button";

export default {
  name: "Demo",
  components: {
    Toggle: Switch,
    Alert,
    TextInput: Input,
    BaseButton: Button
  },
  computed: {
    addingAlertsDisabled() {
      return this.alerts.length >= 3;
    }
  },
  methods: {
    onToggle() {
      this.dangerAlerts = !this.dangerAlerts;
    },
    addAlert() {
      if (!this.currentAlert) {
        this.inputError = true;
        return;
      }
      this.maxId++;
      this.alerts.push({ id: this.maxId, text: this.currentAlert });
      this.currentAlert = "";
    },
    onAlertType(e) {
      if (this.inputError) {
        this.inputError = false;
      }
      this.currentAlert = e.target.value;
    },
    onAlertRemove(id) {
      const index = this.alerts.findIndex(alert => alert.id === id);
      if (index !== -1) {
        this.alerts.splice(index, 1);
      }
    },
    onPressEnter(e) {
      e.preventDefault();
      if (this.addingAlertsDisabled) {
        return false;
      }
      this.addAlert();
    }
  },
  data() {
    return {
      dangerAlerts: false,
      currentAlert: "",
      alerts: [{ text: "Vue is awesome!", id: this.maxId }],
      maxId: 1,
      inputError: false
    };
  }
};
</script>

<style scoped lang="scss">
.demo {
  width: 500px;
  margin: 20px;
  & > * {
    margin-bottom: 20px;
  }

  .alert-container {
    display: flex;
    .toggle-description {
      margin-left: 20px;
    }
  }

  .button-container {
    display: flex;
    .add-button-description {
      margin-left: 20px;
      height: 40px;
      display: flex;
      align-items: center;
    }
  }
}
</style>