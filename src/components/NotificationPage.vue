<template>
  <div class="flex justify-center items-center min-h-screen w-screen">
    <!-- Card -->
    <div class="w-6/12 bg-white rounded-lg shadow-lg p-6">
      <!-- Header -->
      <div class="flex justify-between mb-6 items-end">
        <div class="flex gap-1 items-center">
          <h1 class="font-bold text-lg">Notifications</h1>
          <span
            class="px-2 bg-blue-900 text-white font-semibold rounded-md text-center cursor-pointer"
            >3</span
          >
        </div>
        <span class="text-sm text-gray-500 cursor-pointer"
          >Mark all as read</span
        >
      </div>
      <!-- Content -->
      <div
        v-for="(notif, index) in notifs"
        :key="index"
        class="flex p-4 rounded-md mb-4"
        :class="{
          'bg-slate-100': !notif.hasRead,
          'bg-white': notif.hasRead,
        }">
        <!-- container notif -->
        <div class="flex gap-4 items-start">
          <!-- Avatar -->
          <img
            class="w-10"
            :src="require(`@/assets/images/avatar-${notif.avatar}.webp`)"
            alt="img-profile" />
          <!-- Text -->
          <div>
            <div class="flex gap-2">
              <p v-if="notif.action === 'join'">
                <b>{{ notif.name }}</b> has join your group<b
                  class="text-gray-600">
                  Chese Club</b
                >
              </p>
              <p v-else-if="notif.action === 'follow'">
                <b>{{ notif.name }}</b> followed you
              </p>
              <p v-else>
                <b>{{ notif.name }}</b> sent you a private message
              </p>
              <div
                v-if="notif.hasRead === false"
                class="bg-red-400 rounded-full items-center mt-2 w-3 h-3"></div>
              <div v-else></div>
            </div>
            <div>
              <span class="text-gray-500 text-sm cursor-pointer">{{
                notif.time
              }}</span>
            </div>
            <div
              v-if="notif.action === 'message'"
              class="border-2 border-slate-200 bg-white p-2 rounded-md mt-2">
              <p class="text-gray-500">{{ notif.message }}</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "NotificationPage",

  data() {
    return {
      notifs: [
        {
          name: "Jacob Thompson",
          avatar: "jacob-thompson",
          action: "join",
          time: "1 minutes ago",
          hasRead: false,
        },
        {
          name: "Mark Webber",
          avatar: "mark-webber",
          action: "message",
          time: "5 minutes ago",
          message:
            "Hello, thanks for setting up the Chese Club. I've been a member for a few weeks now and I'm already having lots of fun and improving my game.",
          hasRead: false,
        },
        {
          name: "Anna Kim",
          avatar: "anna-kim",
          action: "follow",
          time: "1 hours ago",
          hasRead: true,
        },
        {
          name: "Angela Gray",
          avatar: "angela-gray",
          action: "message",
          time: "5 days ago",
          message: "Hello, apakah kita bisa berkenalan lebih lanjut ?",
          hasRead: true,
        },
      ],
    };
  },
};
</script>
