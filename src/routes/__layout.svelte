<script>
    import Navbar from '../routes/navbar.svelte';
    import '../app.css';
    import {} from '@fortawesome/fontawesome-free/js/all';
</script>
<Navbar />

<main>
    <slot></slot>
</main>

<footer>
    <p>
    **This website was designed and built by Jorge Fuerte as his personal portfolio website.
    </p>
    <p>
    &copy; Created by
    Jorge Fuerte
    </p>
</footer>

<style>
main{
margin-top: 5rem;
padding: 0;
}

footer {
font-weight: 300;
display: flex;
justify-content: space-evenly;
padding: 2rem;
background: var(--main-maroon);
border-top: 4px solid var(--main-green);
overflow: hidden;
color: white;
}
  
footer > p {
margin: 2rem;
}

@media only screen and (max-width: 600px){
    main{
        margin-top: 4rem;
    }
    footer {
        flex-direction: column;
        text-align: center;
        overflow: hidden;
      }
    footer p{
        font-size: .75rem
    }
}

@media only screen and (max-width: 325px){
    main{
        margin-top: 3rem;
    }
    footer {
        flex-direction: column;
        text-align: center;
        overflow: hidden;
      }
    footer p{
        font-size: .5rem
    }
}

@media only screen and (min-width: 600px){
    footer p{
        font-size: 1rem
    }
}
</style>
