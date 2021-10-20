
<script>
    import { goto } from '$app/navigation';
    import Modal from './modal.svelte';
    import emailjs from 'emailjs-com';
    let modal;

    let fromName;
    let fromEmail;
    let Subject;
    let Message;


    import{ init } from 'emailjs-com';
    init("user_VN8AU6mMd6aMhaObDsmk2");

    function sendMail(params){
        var tempParams = {
        from_name: fromName,
        from_email: fromEmail,
        subject: Subject,
        message: Message,
        }
        emailjs.send('service_6ea4esr', 'template_52md1is', tempParams)
        .then((res) => {
            alert('Email sent succesfully, i`ll get back to you as soon as posible');
            modal.hide();
        }, (error) => {
            modal.hide();
            alert('Email failed to send', error.text);
        })

    }
    // subject, from_name, from_email, message
</script>
<section id="1" class="welcome-section">
    <h1 class="name"><span class="decorator">&lt;</span>Jorge Fuerte<span class="decorator">&#47;&gt;</span></h1>
    <p class="description">Jack of all trades</p>
</section>

<section id="2" class="bio">
    <h1 class="title">Bio</h1>
    <div class="paragraph">
        <p>Not much to say about me, I am college student Just playing around with diferent things, this is my personal website i plan to use to display projects that i am working on, this is the first large project I have done and plan to work on much more so stay tuned to see what i get up to</p>
    </div>
</section>

<section id="3" class="contact">
    <h1 class="name">Let's work together...</h1>
    <p class="description">How do you take you coffee?</p>
    <div class="contact-grid">
        <a href="https://github.com/JorjoF" target="blank">
        <button
        id="profile-link"
        class="contact-details"
        ><i class="fab fa-github"></i>
        GitHub</button></a>

        <button
        on:click={() => modal.show()}
        class="contact-details"
        ><i class="fas fa-at"></i> Send an email</button>

        <a href="resume.pdf" target="blank">
        <button
        id="profile-link"
        class="contact-details"
        ><i class="fas fa-file-alt"></i> My Resume</button></a>
    </div>
</section>

<Modal bind:this={modal}>
    <div class="modal">
        <span class="close" on:click={() => modal.hide() }><i class="fas fa-times fa-2x"></i></span>
        <h1>email me</h1>
        <form class="form" on:submit|preventDefault={() => sendMail()} >
            <div class="form-name">
                <div class="form-name-container">
                    <label for="name">Name:</label>
                    <input id="name" class="form-detail" type="text" bind:value={fromName} placeholder="Name" required>
                </div>
                <div class="form-name-container">
                    <label for="email">Email:</label>
                    <input id="email" class="form-detail"type="email" bind:value={fromEmail} placeholder="Email" required>
                </div>
                <div class="form-name-container">
                    <label for="subject">Subject:</label>
                    <input id="subject" class="form-detail"type="text" bind:value={Subject} placeholder="Subject">
                </div>
            </div>
            <div class="form-text">
                <label for="message">Message:</label>
                <textarea id="message" bind:value={Message} required></textarea>
            </div>
            <button class="form-button"type="submit" > send</button>
        </form>
    </div>
</Modal>

<style>
.welcome-section{
    display: flex;
    flex-direction: column;
    width: 100%;
    height: 100vh;
    justify-content:center;
    align-items: center;
    background-color: black;
    background-image: linear-gradient(62deg, #3a3d40 0%, #181719 100%);
    overflow: hidden;
}

.name{
    color: white;
}

.title{
    font-size: 5rem;
}

.decorator{
    color: #5DFF00;
}
.description{
    font-style: oblique;
    color: white;
}


.bio{
    display: flex;
    flex-direction: column;
    width: 100%;
    height: auto;
    align-items: center;
    background-color: var(--main-gray);
    overflow: hidden;
}

.paragraph{
    display: flex;
    flex-direction: column;
    align-items: center;
    margin-bottom: 5rem;
}
.paragraph p {
    width: clamp(45ch, 50%, 75ch);
}

.contact{
    display: flex;
    flex-direction: column;
    width: 100%;
    height: 100vh;
    justify-content:center;
    align-items: center;
    background-color: var(--main-maroon);
    overflow: hidden;
}

.contact-grid{
    display: grid;
    place-items: center;
    margin-top: 4rem;
    flex-wrap: wrap;
}


.contact-details {
    font-size: 2rem;
    text-shadow: 2px 2px 1px #1f1f1f;
    transition: transform 0.3s ease-out;
    margin: 1rem;
    text-decoration: none;
    color: white;
}
  
.contact-details > i{
    font-size: 2.4rem;
}

.modal{
    display: flex;
    flex-direction: column;
    justify-content: center;
   align-items: center;
}

.close{
        align-self: end;
        cursor: pointer;
        margin: 0 .35rem;
}

.form{
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    row-gap: .5rem;
    width: 60vw;
}

.form-name{
    display: flex;
    justify-content: space-between;
    width: 55vw;
}

.form-name-container{
    display: flex;
    flex-direction: column;
}

.form-detail, .form-text{
    border-radius: .25rem;
}

.form-detail{
    width: 15vw;
}

.form-text{
    display: flex;
    flex-direction: column;
}

.form-button{
    border:solid;
    border-color: black;
    border-radius: .25rem;
    width: 20vw;
}

#message{
    font-family: inherit;
    height: 30vh;
    width: 55vw;
}

@media only screen and (max-width: 600px){
    .contact-grid{
        grid-template-columns: 1fr;
    }

    .contact .name{
        font-size: 2rem;
    }

    .name{
        font-size:3rem;
    }
    .title{
        font-size: 4rem;
    }

    .description{
        font-size: 1.5rem;
    }
    .contact-details, .contact-details > i{
        font-size: 1.5rem;
    }
    
    .paragraph p {
        width: 80%;
        font-size: .8rem;
    }
    .modal{
        height: 75vh;
    }
    .form-name{
        flex-direction: column;
        align-items: center;
    }

    .form-detail{
        width: 55vw;
    }
}

@media only screen and (max-width: 325px){
    .contact-grid{
        grid-template-columns: 1fr;
    }

    .contact .name{
        font-size: 1.5rem;
    }
    .contact .description{
        font-size:1rem;
    }

    .name{
        font-size: 2rem;
    }
    .title{
        font-size: 3rem;
    }

    .description{
        font-size: 1.5rem;
    }
    .contact-details, .contact-details > i{
        font-size: 1.5rem;
    }
    
    .paragraph p {
        width: 80%;
        font-size: .8rem;
    }
}

@media only screen and (min-width: 600px){
    .contact-grid{
        grid-template-columns: 1fr 1fr;
    }
    .contact-details:hover {
        transform: translateY(8px);
    }

    .contact-grid{
        grid-template-columns: 1fr 1fr;
    }

    .contact .name{
        font-size: 5rem;
    }

    .name{
        font-size: 5rem;
    }
    .title{
        font-style: 5rem;
    }

    .description{
        font-size: 2rem;
    }
    .contact-details, .contact-details > i{
        font-size: 2.4rem;
    }
    
    .paragraph p {
        font-size: 1.75rem;
    }
}
</style>