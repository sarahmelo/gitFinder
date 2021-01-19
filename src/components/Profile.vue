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
                <div class="card-body">
                    <a :href="user.html_url" class="btn btn-primary">Ver Perfil</a>
                </div>
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

div.card {
    border: none;
    width: 240px;


    display: flex;
    align-items: center;

    background: #0F1C28;
    box-shadow: 0px 4px 4px rgba(0, 0, 0, 0.4);
    border-radius: 3px;
}

img.card-img-top {
    width: 30%;
    border-radius: 50%;
}

li.list-group-item {
    font-size: smaller;
    align-items: center;
    display: flex;
    border: none;
    padding: 0;
    background-color: transparent;
    margin-top: revert;


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
    background-color: #FC5520;
    margin-left: 10px;
}

div.card.card-body {
    width: auto;
    padding: 8px;
}

</style>