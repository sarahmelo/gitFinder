<template>
    <div class="row">
        <div class="col-md-4">
            <div class="card">
                <img class="card-img-top" :src="user.avatar_url">
                <ul class="list-group list-group-flush">
                    <li class="list-group-item">
                        Repositórios: <span class="badge badge"> {{ user.public_repos}}</span>
                    </li>
                    <li class="list-group-item">
                        Seguidores: <span class="badge badge"> {{ user.followers }}</span>
                    </li>
                    <li class="list-group-item">
                        Seguindo: <span class="badge badge"> {{ user.following }}</span>
                    </li>
                </ul>
            </div>

            <div class="card-body">
                    <a :href="user.html_url" class="btn">Ver Perfil</a>
                </div>

        </div>
    </div>
</template>

<script>
export default {
    props: ['user']
}
</script>

<style>

a.btn {
    background-color: #676767;
    color: #1F1F1F;
    border-radius: 1rem;
}


div.card {
    
    width: 320px;
    padding: 30px;
    border: none;
    border-radius: 15px 15px 0 0;
    background-image: url('../assets/wallpaper.jpg');
    box-shadow: 0px 4px 4px rgba(0, 0, 0, 0.25);

    /* #404040 */
    display: flex;
    flex-direction: inherit;
    align-items: center;
}

img.card-img-top {
    width: 30%;
    border-radius: 50%;
    margin-left: inherit;
}

li.list-group-item {
   
    font-size: smaller; 
    display: flex;
    border: none;
    padding: 0;
    background-color: transparent;
    margin-top: revert;
    margin-left: 20%;
    align-items: center;
    color: white;
}

#text {
    
    font-size: smaller;
    align-items: center;
    display: flex;
}

span.badge.badge {
    
    border-radius: 50%;
    height: 20px;
    width: 20px;
    align-items: center;
    display: flex;
    margin-left: 10px;
}

div.card.card-body {
   
    width: auto;
    padding: 8px;
}

div.card-body {
    
    place-content: center;
    background-color: #080808;
    width: 320px;
    display: flex;
    height: 64px;
    padding: 8px;
    align-items: center;
}

</style>