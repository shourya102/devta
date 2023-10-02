<script>
import {settingsList} from "@/SettingsModal/settingsList.js";

export default {
  props: {
    isMobile: Boolean
  },
  methods: {
    settingsList() {
      return settingsList
    },
    close() {
      this.$emit('close');
    },
    saveData() {
      this.$emit('save');
    }
  }
};
</script>

<template>
  <div v-if="isMobile">

  </div>
  <div v-else class="modal-backdrop bg-black bg-opacity-50">
    <div id="settings" aria-hidden="true"
         aria-labelledby="settingsModal" class="modal" role="dialog"
         style="display: block;" tabindex="-1">
      <div class="modal-dialog modal-xl mh-100" role="document">
        <div class="modal-content">
          <div class="modal-header">
            <h5 id="settings-heading" class="modal-title bi bi-gear"> Settings</h5>
            <button aria-label="Close" class="btn btn-close" data-dismiss="modal" type="button" @click=close>
            </button>
          </div>
          <div class="modal-body d-flex flex-row">
            <ul class="nav nav-pills flex-column gap-1">
              <div v-for="(item, index) in settingsList()" :key="index">
                <li class="nav-item">
                  <button :title=item.tooltip class="btn-item" type="button">{{ item.title }}</button>
                </li>
              </div>
            </ul>
            <div class="block card w-100">

            </div>
          </div>

          <div class="modal-footer">
            <button class="btn btn-secondary" data-dismiss="modal" type="button" @click=close>Close</button>
            <button class="btn btn-primary" type="button" @click=saveData>Save changes</button>
          </div>
        </div>
      </div>
    </div>
  </div>

</template>

<style scoped>

.btn-item {
  padding: 0.6rem;
  margin-bottom: 3px;
  margin-right: 1.2rem;
  background-color: transparent;
  border: none;
}

.btn-item:hover {
  background-color: rgb(108, 117, 125);
  border-radius: 5px;
}

.btn-item:focus {
  background-color: var(--bs-blue);
  border-radius: 5px;
}
</style>