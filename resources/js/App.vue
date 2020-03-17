<template>
    <div>
        <router-view />
    </div>
</template>

<script>
    import { CometChat } from "@cometchat-pro/chat";
    export default {
        created() {
            this.initializeApp();
        },

        // initializing cometchats sdk so as to make it easy for us to connect with their servers
        methods: {
            initializeApp() {
                let appID = process.env.MIX_COMMETCHAT_APP_ID;

                let cometChatSettings = new CometChat.AppSettingsBuilder()
                    .subscribePresenceForAllUsers()
                    .setRegion("eu")
                    .build();

                CometChat.init(appID, cometChatSettings).then(
                    () => {
                        console.log("Initialization completed successfully");
                    },
                    error => {
                        console.log("Initialization failed with error:", error);
                    }
                );
            }
        }
    };
</script>

<style scoped>

</style>
