<!-- Import necessary modules -->
<!-- -------------------------------------------------------------(THIS PART FOR REMOVE PEER-ID INVALID)---------------------- -->
<script type="text/javascript">
    import pyrogram.utils as utils;  // Importing Pyrogram utils

    // Custom get_peer_type function
    function get_peer_type(peer_id) {
        console.log('get_peer_type call');
        let peer_id_str = peer_id.toString();
        if (!peer_id_str.startsWith("-")) {
            return "user";
        } else if (peer_id_str.startsWith("-100")) {
            return "channel";
        } else {
            return "chat";
        }
    }

    // Overriding the Pyrogram's get_peer_type with your custom function
    utils.get_peer_type = get_peer_type;
</script>
<!-- -------------------------------------------------------------------------------------------------------------------------- -->

<!-- Original bot.py/main.py code continues.... -->

<!-- Your existing script continues from here... -->
