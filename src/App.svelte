<script>
    import "./app.css";
    import profilePic from "./assets/ProfilePic.jpg";
    import Link from "./lib/Link.svelte";

    let texts = [
        "Software Developer",
        "Web Developer",
        "Front End Developer",
        "Programmer",
    ];
    let index = 0;
    let currentText = texts[index];

    setInterval(() => {
        index = (index + 1) % texts.length;
        currentText = texts[index];
    }, 2000);
</script>

<main>
    <img src={profilePic} alt="Profile avatar" />
    <div class="name-and-location">
        <h1>Juan Cruz Caceres</h1>
        <p class="location">Argentina</p>
    </div>
    <p class="description">"{currentText}"</p>
    <div class="links">
        <Link href="https://github.com/YsmaelOutis" text="GitHub" />
        <Link href="https://www.frontendmentor.io/profile/YsmaelOutis" text="Frontend Mentor" />
        <Link href="https://www.linkedin.com/in/juan-cruz-caceres-1a5620237/" text="Linkedin" />
        <Link href="https://app.netlify.com/teams/ysmaeloutis/sites" text="Netlify" />
    </div>
</main>
