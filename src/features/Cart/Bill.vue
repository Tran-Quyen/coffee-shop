<template>
  <div class="col-md-4">
    <div
      class="osahan-cart-item rounded rounded shadow-sm overflow-hidden bg-white sticky_sidebar"
    >
      <div class="d-flex border-bottom osahan-cart-item-profile bg-white p-3">
        <VImg
          alt="osahan"
          src="img/starter1.jpg"
          class="mr-3 rounded-circle img-fluid"
        />
        <div class="d-flex flex-column">
          <h6 class="mb-1 font-weight-bold">Nhà Hàng Nam & Khánh</h6>
          <p class="mb-0 small text-muted">
            <i class="feather-map-pin"></i> 1 Võ văn Ngân, Thủ Đức, TP.HCM
          </p>
        </div>
      </div>
      <div class="bg-white border-bottom py-2">
        <div
          v-for="cart in $store.getters.getCart.items"
          :key="cart.id"
          class="gold-members d-flex align-items-center justify-content-between px-3 py-2"
        >
          <div class="media align-items-center">
            <div class="mr-2 text-success">&middot;</div>
            <div class="media-body">
              <p class="m-0">
                {{ cart.product.name }}
              </p>
            </div>
          </div>
          <div class="d-flex align-items-center">
            <span class="count-number float-right">
              <input-quantity :cart="cart" />
            </span>
            <p class="text-gray mb-0 float-right ml-2 text-muted small">
              {{ cart.subtotal_format }}
            </p>
            <button-delete-cart
              :cart-id="cart.id"
              class="ml-2 text-danger outline-none"
            >
              <i class="feather-x-circle"></i>
            </button-delete-cart>
          </div>
        </div>
      </div>
      <div class="bg-white p-3 py-3 border-bottom clearfix">
        <!-- <div class="input-group-sm mb-2 input-group">
          <input
            placeholder="Nhập mã giảm giá"
            type="text"
            class="form-control"
          />
          <div class="input-group-append">
            <button type="button" class="btn btn-primary">
              <i class="feather-percent"></i> Xác nhận
            </button>
          </div>
        </div> -->
        <div id="customerNote"></div>
      </div>
      <div class="bg-white p-3 clearfix border-bottom">
        <p v-if="$store.getters.getCart.delivery_fee" class="mb-1">
          Tổng tiền
          <span class="float-right text-dark">
            {{ $store.getters.getCart.total_format }}
          </span>
        </p>
        <p v-if="$store.getters.getCart.delivery_fee" class="mb-1">
          Phí vận chuyển
          <span class="float-right text-dark">
            {{ $store.getters.getCart.delivery_fee_format }}
          </span>
        </p>
        <hr v-if="$store.getters.getCart.delivery_fee" />
        <h6 class="font-weight-bold mb-0">
          Thực thu
          <span class="float-right">
            {{ $store.getters.getCart.grand_total_format }}
          </span>
        </h6>
      </div>
      <!-- teleport -->
      <div id="btnSubmitCheckout" class="p-3"></div>
    </div>
  </div>
</template>

<script>
import ButtonDeleteCart from "@/components/buttons/ButtonDeleteCart";
import InputQuantity from "@/components/InputQuantity";

export default {
  components: {
    ButtonDeleteCart,
    InputQuantity,
  },
};
</script>
