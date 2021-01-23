<template>

    <div class="card card-body mb-2">
        <div class="row">
            <div class="col-md">
                <a :href=" repo.html_url" target="_blank"> {{ repo.name }}</a>
            </div>
            <!-- <div class="col-md-6">
                <span> Stars: {{ repo.stargazers_count }}</span>
                <span class="badge badge-primary"> Watch: {{ repo.watchers_count }}</span>
                <span class="badge badge-primary"> Forks: {{ repo.forks_count }}</span>
            </div> -->
        </div>
    </div>
    
</template>

<script>
export default {
    props: ['repo']
};
</script>

<style>

a {
    padding: inherit;
}

div.row {
    width: -webkit-fill-available;
}

div.card.card-body.mb-2 {
    
    display: flex;
    align-items: stretch;
    background: transparent;
    box-shadow: none;
    border-radius: 3px;
    height: 50px;
    margin-bottom: 20px;
}

div.col-md-8 {
    
    max-width: 320px;
    height: 175;
    background-color: #080808;
    box-shadow: 0px 4px 4px rgba(0, 0, 0, 0.25);
}

a:link {
    
    font-size: smaller;
    color: white;
    text-decoration: none;

}

a:visited {
    
    color: white;
    text-decoration: none;
}

::-webkit-scrollbar {
  width: 5px;
  border: none;
}

/* Track */
::-webkit-scrollbar-track {
  border-radius: 10px;
}

/* Handle */
::-webkit-scrollbar-thumb {
  background: #cecece;
  border-radius: 10px;
}

/* Handle on hover */
::-webkit-scrollbar-thumb:hover {
  background: #4d6880;
}

</style>