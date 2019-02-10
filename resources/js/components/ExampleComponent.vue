<template>
    <div class="container">
        <div class="row justify-content-center">
            <div class="col-md-8">
                <div class="card card-default">
                    <div class="card-header">Example Component</div>

                    <div class="card-body">
                        I'm an example component.
                    </div>

                    <ul v-if="messages.length > 0">
                        <li v-for="message in messages">{{ message }}</li>
                    </ul>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    export default {

        data() {
            return {
                messages: []
            }
        },

        mounted() {

            window.Echo.channel('chat').listen('OnMessageSent',(e) => {
                console.log(e);
                this.messages.push(e.message);
            });

        }
    }
</script>
