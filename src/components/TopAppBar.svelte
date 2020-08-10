<script>
    import IconButton from '@smui/icon-button';
    import TopAppBar, { Row, Section, Title } from '@smui/top-app-bar';
    import { currentUser } from '../stores/user';
    let activeUser;
    currentUser.subscribe( ( user ) => {
        activeUser = user;
    } );

    function login() {
        const path = location.pathname;
        location = `/login?nextUrl=${path}`;
    }

    function logout() {
        firebase
        .auth()
        .signOut()
        .then(async function() {
            window.location.replace('/login');
        })
        .catch(function(error) {
            // An error happened.
            alert(error);
        });
    }
</script>

<div class="top-app-bar-container">
    <TopAppBar variant="fixed">
        <Row>
            <Section>
                <IconButton class="material-icons">menu</IconButton>
            </Section>
            <Section align="end" toolbar>
                { #if activeUser !== null }
                    <IconButton class="material-icons" on:click={ logout }>exit_to_app</IconButton>
                { :else }
                    <IconButton class="material-icons" on:click={ login }>login</IconButton>
                { /if }
            </Section>
        </Row>
    </TopAppBar>
</div>