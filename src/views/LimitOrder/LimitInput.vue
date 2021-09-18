<template>
  <div class="swap-send-container">
    <div class="swap-send-main">
      <div class="swap-send-main-input-container">
        <div class="swap-send-main-input">
          <div class="swap-send-top">
          <div class="swap-send-top-label">
            Limit
          </div>
          <div class="swap-send-top-amount" style="display:none">
            <div class="btn btn-option label-append" >
              <span :style="getAssetColorStyle(asset)">
                Current
              </span>
            </div>
          </div>
      </div>
        <input
          type="number"
          class="form-control"
          id="swap_limit_amount_input_field"
          :class="{ 'is-invalid': showErrors && amountError }"
          :value="limitAmount"
          @input="$emit('update:limitAmount', $event.target.value)"
          placeholder="0.00"
          :style="getAssetColorStyle(asset)"
          autocomplete="off"
          :disabled="disabled"
        />
        </div>
      </div>
      <div class="swap-send-main-errors" v-if="showErrors && amountError">
        <small class="text-danger form-text text-right">
          {{ amountError }}
        </small>
      </div>
    </div>
  </div>
</template>

<script>
import { getAssetColorStyle, getAssetIcon } from '@/utils/asset'
import { dpUI } from '@/utils/coinFormatter'
import ChevronRightIcon from '@/assets/icons/chevron_right_gray.svg'
import AccountTooltip from '@/components/AccountTooltip'

export default {
  components: {
    ChevronRightIcon,
    AccountTooltip
  },
  data () {
    return {
    }
  },
  props: [
    'account',
    'asset',
    'available',
    'limitAmount',
    'showErrors',
    'amountError',
    'disabled',
    'amountOption'
  ],
  created () {},
  methods: {
    dpUI,
    getAssetColorStyle,
    getAssetIcon,
  }
}
</script>

<style lang="scss">
.swap-send-container {
  display: flex;
  flex-direction: column;
  width: 100%;

  .swap-send-top {
    display: flex;
    justify-content: space-between;

    .swap-send-top-label {
      font-size: 0.75rem;
      font-weight: bold;
      text-transform: uppercase;
    }
  }

  .swap-send-main {
    display: flex;
    flex-direction: column;
    .swap-send-main-input-container {
      display: flex;
      justify-content: space-between;

      .swap-send-main-input {
        display: flex;
        flex-direction: column;
        max-width: 190px;
      }
    }

    .swap-send-main-icon {
      cursor: pointer;
      display: flex;
      align-items: flex-end;
      justify-content: space-between;
      margin-left: 10px;

      .asset-name {
        margin-left: 5px;
        font-style: normal;
        font-weight: 300;
        font-size: 24px;
        line-height: 24px;
      }

      div {
        display: flex;
        align-items: center;
        height: 24px;

        svg {
          width: 8px;
          margin-left: 10px;
          vertical-align: middle;
        }
      }
    }

    .swap-send-main-errors {
      display: flex;
      width: 100%;
    }

  }
}
</style>
