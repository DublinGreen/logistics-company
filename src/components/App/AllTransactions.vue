<template>
  <div
    class="relative flex flex-col min-w-0 break-words bg-white w-full mb-6 rounded"
  >
    <div class="pt-6 pb-4 px-6">
      <div class="flex -mx-2">
        <div class="w-full pr-2">
          <div class="row">
            <div class="col-md-3">
              <div class="font-bold text-base">All Transactions</div>
            </div>
            <div class="col-md-9">
              <div class="text-right">
                <vs-select
                  class="selectExample d-inlineblock mr-3"
                  v-model="filterDate"
                >
                  <vs-select-item
                    :key="index"
                    :value="item.value"
                    :text="item.text"
                    v-for="(item, index) in filterSel"
                  />
                </vs-select>
                <vs-input
                  class="d-inlineblock mr-3 siteFormIcon"
                  icon-no-border
                  icon="search"
                  placeholder="Search"
                  v-model="seachfield"
                />
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
    <div class="block w-full overflow-x-auto">
      <!-- Projects table -->
      <table class="items-center w-full bg-transparent border-collapse">
        <thead>
          <tr>
            <th
              class="px-6 bg-gray-100 text-gray-600 align-middle border border-solid border-gray-200 py-3 text-xs uppercase border-l-0 border-r-0 whitespace-no-wrap font-semibold text-left"
            >
              Date
            </th>

            <th
              class="px-6 bg-gray-100 text-gray-600 align-middle border border-solid border-gray-200 py-3 text-xs uppercase border-l-0 border-r-0 whitespace-no-wrap font-semibold text-left"
            >
              Amount
            </th>

            <th
              class="px-6 bg-gray-100 text-gray-600 align-middle border border-solid border-gray-200 py-3 text-xs uppercase border-l-0 border-r-0 whitespace-no-wrap font-semibold text-left"
            >
              Status
            </th>
            <th
              class="px-6 bg-gray-100 text-gray-600 align-middle border border-solid border-gray-200 py-3 text-xs uppercase border-l-0 border-r-0 whitespace-no-wrap font-semibold text-left"
            >
              Client
            </th>
            <th
              class="px-6 bg-gray-100 text-gray-600 align-middle border border-solid border-gray-200 py-3 text-xs uppercase border-l-0 border-r-0 whitespace-no-wrap font-semibold text-left"
            >
              Rider
            </th>
            <th
              class="px-6 bg-gray-100 text-gray-600 align-middle border border-solid border-gray-200 py-3 text-xs uppercase border-l-0 border-r-0 whitespace-no-wrap font-semibold text-left"
            >
              Action
            </th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="(order, index) in orders" :key="index">
            <th
              class="border-t-0 px-6 align-middle border-l-0 border-r-0 text-xs whitespace-no-wrap p-4 text-left"
            >
              <p class="text-gray-500">{{ order.date }}</p>
            </th>

            <td
              class="border-t-0 px-6 align-middle border-l-0 border-r-0 text-xs whitespace-no-wrap p-4"
            >
              <p>{{ order.amount }}</p>
            </td>
            <td class="border-t-0 px-6 align-middle border-l-0 border-r-0 p-4">
              <span
                class="f-10 font-semibold inline-block py-1 px-2 uppercase rounded text-green-600 bg-green-200 uppercase last:mr-0 mr-1"
              >
                Successful
              </span>
            </td>
            <td
              class="border-t-0 px-6 align-middle border-l-0 border-r-0 text-xs whitespace-no-wrap p-4"
            >
              <p>{{ order.client }}</p>
            </td>

            <td
              class="border-t-0 px-6 align-middle border-l-0 border-r-0 text-xs whitespace-no-wrap p-4"
            >
              <p>Kayode Salam</p>
            </td>
            <td
              class="border-t-0 px-6 align-middle border-l-0 border-r-0 text-xs whitespace-no-wrap p-4"
            >
              <button
                class="bg-primary text-capitalize text-white active:bg-green-600 font-bold text-xs px-4 py-2 rounded shadow hover:shadow-md outline-none focus:outline-none mr-1 mb-1 ease-linear transition-all duration-150"
                type="button"
                @click="$store.commit('viewTransaction', true)"
              >
                View
              </button>

              <!-- <button
                class="text-primary bg-transparent border border-solid border-green-500 hover:bg-green-500 hover:text-white active:bg-green-600 font-bold text-capitalize text-xs px-4 py-2 rounded outline-none focus:outline-none mr-1 mb-1 ease-linear transition-all duration-150"
                type="button"
              >
                Export
              </button> -->

              <button
                class="text-primary bg-transparent border border-solid border-green-500 hover:bg-green-500 hover:text-white active:bg-green-600 font-bold uppercase text-xs px-4 py-2 rounded outline-none focus:outline-none mr-1 mb-1 ease-linear transition-all duration-150"
                type="button"
              >
                <i class="fa fa-ellipsis-v"></i>
              </button>
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>
<script>
export default {
  mounted: function () {},
  data() {
    return {
      filterDate: 1,
      seachfield: "",
      filterSel: [
        { text: "All", value: 1 },
        { text: "Successful", value: 2 },
        { text: "Pending", value: 3 },
        { text: "Failed", value: 3 },
      ],
      orders: [
        {
          product: "Hp 15 AMD ",
          date: "2 mins ago",
          orderBy: "#j233131j22",
          amount: "N12,033",
          client: "Mr. Oluwafemi",
          img:
            "https://ng.jumia.is/unsafe/fit-in/300x300/filters:fill(white)/product/98/092975/1.jpg?1093",
        },
        {
          product: "Imose Zedon ",
          date: "2 mins ago",
          orderBy: "#j233131j22",
          amount: "N12,033",
          client: "Mr. Oluwafemi",
          img:
            "https://ng.jumia.is/unsafe/fit-in/500x500/filters:fill(white)/product/82/294222/1.jpg?3658",
        },
        {
          product: "290 G2 ",
          date: "2 mins ago",
          orderBy: "#j233131j22",
          amount: "N12,033",
          client: "Mr. Oluwafemi",
          img:
            "https://ng.jumia.is/unsafe/fit-in/500x500/filters:fill(white)/product/73/853565/1.jpg?5348",
        },
        {
          product: "Hp Deskjet Ink",
          date: "2 mins ago",
          orderBy: "#j233131j22",
          amount: "N12,033",
          client: "Mr. Oluwafemi",
          img:
            "https://ng.jumia.is/unsafe/fit-in/500x500/filters:fill(white)/product/31/566564/1.jpg?2314",
        },
        {
          product: "Hp 15 AMD ",
          date: "2 mins ago",
          orderBy: "#j233131j22",
          amount: "N12,033",
          client: "Mr. Oluwafemi",
          img:
            "https://ng.jumia.is/unsafe/fit-in/300x300/filters:fill(white)/product/98/092975/1.jpg?1093",
        },
        {
          product: "Imose Zedon ",
          date: "2 mins ago",
          orderBy: "#j233131j22",
          amount: "N12,033",
          client: "Mr. Oluwafemi",
          img:
            "https://ng.jumia.is/unsafe/fit-in/500x500/filters:fill(white)/product/82/294222/1.jpg?3658",
        },
      ],
    };
  },
};
</script>
