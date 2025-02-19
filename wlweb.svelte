<script>
    let age = "";
    let steam = "";
    let discord = "";
    let question1 = "";
    let question2 = "";
    let question3 = "";
	let question4 = "";
	let question5 = "";
    let errorMessage = "";

    const validateAndSubmit = async () => {
        if (!age || !steam || !discord || !question1 || !question2 || !question3 || !question5 || !question4) {
            errorMessage = "Please fill all fiels before submitting!";
            return;
        }

        errorMessage = "";

        const payload = {
            content: `New Whitelisted application received!\n**Age:** ${age}\n**Steam:** ${steam}\n**Discord:** ${discord}\n**YOUR-QUESTION-HERE:** ${question1}\n**YOUR-QUESTION-HERE:** ${question2}\n**YOUR-QUESTION-HERE:** ${question3}\n**YOUR-QUESTION-HERE:** ${question4}\n**YOUR-QUESTION-HERE:** ${question5}`
        };

        const webhookURL = 'https://discord.com/api/webhooks/1341845924774936707/6YD4i_mDDrAaj22Nm2V86oL7FfKmuP5tEdedl4HIBr9twvXQPQ6j0Ml5cbLp4wn8jbHL'; // Replace with your actual URL

        try {
            const response = await fetch(webhookURL, {
                method: 'POST',
                headers: {
                    'Content-Type': 'application/json'
                },
                body: JSON.stringify(payload)
            });

            if (response.ok) {
                alert('Form submitted successfully!');
                age = '';
                steam = '';
                discord = '';
                question1 = '';
                question2 = '';
                question3 = '';
            } else {
                alert('Failed to submit form. Please try again later.');
            }
        } catch (error) {
            console.error('Error sending to Discord webhook:', error);
            alert('There was an error submitting the form. Please try again later.');
        }
    };
</script>

<main class="container">
    <h1 class="title">Whitelist Application</h1>

    <label for="age">Age:</label>
    <input type="number" bind:value={age} min="1" required />

    <label for="steam">Steam Profile:</label>
    <input type="url" bind:value={steam} required />

    <label for="discord">Discord:</label>
    <input type="text" bind:value={discord} required />

    <label for="question1">YOUR-QUESTION-HERE</label>
    <input type="text" bind:value={question1} required />

    <label for="question2">YOUR-QUESTION-HERE</label>
    <input type="text" bind:value={question2} required />

    <label for="question3">YOUR-QUESTION-HERE</label>
    <input type="text" bind:value={question3} required />

	<label for="question4">YOUR-QUESTION-HERE</label>
    <input type="text" bind:value={question4} required />

	<label for="question5">YOUR-QUESTION-HERE</label>
    <input type="text" bind:value={question5} required />

    {#if errorMessage}
        <p class="error">{errorMessage}</p>
    {/if}

    <button id="submit-btn" class="submit-btn" on:click={validateAndSubmit}>Submit</button>
</main>

<style>
    .container {
        max-width: 400px;
        margin: auto;
        padding: 20px;
        border-radius: 10px;
        background-color: #2c2f33;
        color: #ffffff;
        box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
    }

    .title {
        text-align: center;
        color: violet;
    }

    label {
        display: block;
        margin: 10px 0 5px;
        font-weight: bold;
    }

    input {
        width: 100%;
        padding: 10px;
        margin-bottom: 15px;
        border: 1px solid #ccc;
        border-radius: 5px;
    }

    .error {
        color: red;
        font-weight: bold;
        text-align: center;
    }

    .submit-btn {
        width: 100%;
        padding: 10px;
        background-color: #7289da;
        color: white;
        border: none;
        border-radius: 5px;
        cursor: pointer;
        transition: background-color 0.3s;
    }

    .submit-btn:hover {
        background-color: #5a6bbf;
    }
</style>
