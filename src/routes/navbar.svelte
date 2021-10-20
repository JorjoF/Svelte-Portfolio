<script>
function smoothScrolling(target, duration){
    var target = target;
    ;
    console.log(target)
}
</script>



<nav id="navbar" class="nav">
    <ul class="nav-list">
        <li class="nav-item">
            <a href='#1'  class="nav-link">About</a>
        </li>
        <li class="nav-item">
            <a href="#2"  class="nav-link">Portfolio</a>
        </li>
        <li class="nav-item">
            <a href="#3"  class="nav-link">Contact</a>
        </li>
    </ul>
</nav>

<style>
.nav{
    height: 5rem;
    width: 100vw;
    top: 0;
    position: fixed;
    background-color: var(--main-green);
}

.nav-list{
    list-style: none;
    padding: 0;
    margin: 0;
    display: flex;
    justify-content: flex-end;
}

.nav-item{
    height: 100%;
}

.nav-link{
    display: flex;
    align-items: center;
    height: 5rem;
    padding: 0 1rem;
    color: white;
    font-size: 2rem;
    font-weight: bold;
    text-decoration: none;
}


@media only screen and (max-width: 600px){
    .nav{
        height: 4rem;
    }
    .nav-list{
        justify-content: center;
    }
    .nav-link{
        font-size: 1.50rem;
        height: 4rem;
    }
}

@media only screen and (max-width: 325px){
    .nav{
        height: 3rem;
    }
    .nav-list{
        justify-content: center;
    }
    .nav-link{
        font-size: 1.25rem;
        height: 3rem;
        padding: 0 .75rem;
    }
}

@media only screen and (min-width: 600px){
    .nav-link:hover{
        background-color: var(--main-darkgreen);
    }
}
</style>