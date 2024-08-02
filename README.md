<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Main Page</title>
    <style>
        body {
            background: linear-gradient(45deg, #ff6f61, #dce35b);
            color: #333;
            font-family: Times New Roman, serif;
            text-align: center;
            padding: 20px;
        }
        h1 {
            font-size: 2em;
        }
        p {
            font-size: 1.2em;
        }
        form {
            margin: 20px 0;
        }
        input[type="text"] {
            font-size: 1.2em;
            padding: 10px;
            margin: 10px 0;
            border: 2px solid #333;
            border-radius: 5px;
        }
        button {
            font-size: 1.2em;
            padding: 10px 20px;
            background-color: #333;
            color: #fff;
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }
        button:hover {
            background-color: #555;
        }
        #response {
            font-size: 1.2em;
            margin-top: 20px;
        }
        a {
            color: #ff6f61;
            text-decoration: none;
        }
        a:hover {
            text-decoration: underline;
        }
        .designer {
            margin-top: 20px;
            font-size: 1em;
            color: #666;
        }
    </style>
</head>
<body>
    <h1>Welcome to Wonder World</h1>
    <p>NOTE: Only the 2024 set of Total Child Secondary School can input their names.</p>
    
    <form id="details-form">
        <label for="full-name">Please enter your full name (for example: surname_firstname):</label><br>
        <input type="text" id="full-name" name="full-name" required><br>
        <button type="submit">Submit</button>
    </form>

    <div id="response"></div>

    <div class="designer">
        Designed by <strong>WONDER</strong>
    </div>

    <script>
    var statuses = {
        "Abolude Testimony": "A bright light in our classroom, Abito embodied a serene spirit, radiant heart, and curious soul. With a deep connection to the world's wonders, they inspired us to explore, dream, and grow. Their presence was a blessing, leaving an indelible mark on our lives and hearts.",
        "Adewuyi Marvellous": "A calm and intelligent girl, with a gentle spirit and a sweet smile. She had a soft presence that put others at ease, and a quiet confidence that inspired respect. Her thoughtful nature and curious mind made her a joy to be around.",
        "Adeyanju Enoch": "A calm and curious boy, with a gentle soul and a thirst for knowledge. He had a quiet confidence and patient nature, reminiscent of a wildlife observer, able to sit still and observe the world around him with wonder and curiosity.",
        "Ajayi Emmanuel": "A boy with a strong and lean physique, honed from years of active play and sports. His athletic build and agile movements spoke to his love of physical activity, and his coordination and balance hinted at a natural talent for competition. With a quiet confidence and calm demeanor, he moved with a sense of purpose and poise, always ready to take on the next challenge.",
        "Alabi Adedamola": "He walked with a confident air, his relaxed stride and effortless cool making him hard to miss. But he was never too full of himself, thanks to a quick wit and a humorous streak that kept him grounded. He had a way of making everyone feel at ease, whether he was cracking jokes or simply being his laid-back self. With a grin that could light up a room, He was the kind of guy who made a lasting impression – without ever trying too hard.",
        "Ayanda Joseph": "A fair-complexioned boy with a confident and self-assured demeanor. While he sometimes acts on impulse, his charming and endearing personality shines through, making him a great person to be around. His confidence and positivity are infectious, and his imperfections only add to his relatable and human charm.",
        "Ayenuberun Peace": "A vibrant and lively boy with a remarkable gift for public speaking. As a skilled orator, he has a way with words, captivating his audience with his confident tone, articulate expression, and passionate delivery. His lively nature makes him a compelling and engaging presence, able to inspire and motivate others with his words.",
        "Ayinde Emmanuel": "A quiet and introspective young individual who embodies great responsibility and brilliance. With a keen mind and strong sense of duty, he tackles challenges with maturity and poise, achieving impressive accomplishments. His humility and soft-spoken nature give him a quiet confidence that commands respect.",
        "Babawale Elijah": "A vibrant and charismatic individual who lights up the room with his infectious humor and effortless charm. But don't let his playful demeanor fool you - when he turns serious, he transforms into a focused and driven achiever, tackling challenges with determination and excellence. With a unique blend of humor, humility, and hustle, he makes a lasting impact on those around him.",
        "Babawale Elizabeth": "A bright and bubbly girl who spreads joy and positivity wherever she goes, with a contagious laugh that's simply infectious! But don't underestimate her playful nature - she's also a fierce and focused competitor, driven to succeed in all her life pursuits. With a heart full of joy and a spirit that never quits, she tackles every challenge with a smile and a spring in her step.",
        "Bello Israel": "Cool, charming, and ridiculously talented - this rapper's got it all. Smooth flow, sharp style, and a voice that's pure magic. He's got the swagger of a superstar and the heart of a poet - a deadly combination that's taking the music world by storm. And with a coolness that's effortless and authentic, he's the total package: talent, looks, and a chill vibe that's impossible to resist.",
        "Bello Olaseni": "He has a sturdy build and a confident air, with a well-groomed appearance that suggests a life of comfort and privilege. His features are refined and well-defined, with a poised and self-assured expression that commands respect. Despite his youth, he carries himself with the great confidence of someone who knows they are well-provided for.",
        "Fatile Taye": "A funny and charming guy with a voice like an angel, often found on his own, but never lonely. He brightens up the atmosphere with his humor and singing. His blast-off of the Y-language is a spread of laughing gas in the air. With a heart full of kindness and a spirit that's always uplifting, he spreads love and laughter wherever he goes, one smile and song at a time.",
        "Mepaiyeda Boluwatife": "A true embodiment of courage and conviction. He possesses a fearless spirit, never hesitating to speak his mind and stand up for what he believes in, even in the face of adversity. Through his actions, he inspires others to be brave, to speak their truth, and to fight for what is just. His presence is a reminder that one person can make a difference, and that collective courage can lead to meaningful change.",
        "Oladotun Esther": "A sweet and adorable girl with a gentle soul. Her calm and soothing presence makes her a joy to be around. With a heart full of love and a light spirit, she's a compassionate and beloved friend. Her easy-going nature and warm smile can brighten up anyone's day, making her a treasured companion to all who know her.",
        "Omotola Iretomiwa": "A compact ball of confidence, standing at a height that may be below average, but his ego and self-assurance tower above the rest. His diminutive stature is vastly overshadowed by his larger-than-life personality, and his sharp wit and clever banter can leave others in awe. Despite his physical height, he has a gigantic presence that commands attention and respect, and he knows exactly how to use it to his advantage.",
        "Owolabi Praise": "He stands tall, with a commanding presence that's hard to ignore. He exudes a calm and gentle demeanor, moving with a relaxed ease that puts those around him at ease. His easy-going nature makes him approachable and likable, but don't let that fool you - beneath his laid-back exterior lies a fiercely ambitious drive, constantly pushing him to strive for excellence and reach new heights.",
        "Usman Jeffrey": "He has a relaxed and effortless charm, moving through life with a gentle ease that makes him a joy to be around. But beneath his laid-back exterior lies a sharp and agile mind, capable of tackling complex ideas and solving intricate problems with ease. His intelligence is subtle, yet unmistakable. He's the perfect blend of book smarts and street smarts, with a quick wit and a warm heart."
    };

    var nicknames = {
        "Abolude Testimony": "Pastor",
        "Adewuyi Marvellous": "Marvy",
        "Adeyanju Enoch": "Obobs",
        "Ajayi Emmanuel": "EBA",
        "Alabi Adedamola": "Damoch",
        "Ayanda Joseph": "Holy keyz",
        "Ayenuberun Peace": "Qualme",
        "Ayinde Emmanuel": "Ayinzy",
        "Babawale Elijah": "Kenny blaq",
        "Babawale Elizabeth": "Dammy",
        "Bello Israel": "De legend",
        "Bello Olaseni": "Bullion van",
        "Fatile Taye": "Private life",
        "Mepaiyeda Boluwatife": "Human Right Activist",
        "Oladotun Esther": "Xstar",
        "Omotola Iretomiwa": "Tomzy Alex",
        "Owolabi Praise": "P-money",
        "Usman Jeffrey": "Wonder"
    };

    document.getElementById('details-form').addEventListener('submit', function(event) {
        event.preventDefault();
        var fullName = document.getElementById('full-name').value.trim();

        // Input validation
        if (fullName === "") {
            alert("Please enter your full name (For example: surname_firstname)");
            return;
        }

        var nickname = nicknames[fullName];
        var status = statuses[fullName];

        if (nickname) {
            var response = "How are you today? Do you want to view your status as the set2k24 of Total Child Secondary School?";
            response += "<br><a href='#' onclick='showStatus(\"" + fullName + "\")'>Yes</a>";
            response += "<br><a href='#' onclick='showSorry()'>No</a>";
            document.getElementById('response').innerHTML = response;
        } else {
            showSorry();
        }
    });

    function showStatus(fullName) {
        var status = statuses[fullName];
        if (status) {
            document.getElementById('response').innerHTML = "<h1>Status</h1><p>" + status + "</p><a href='#' onclick='goBack()'>Main Page</a>";
        } else {
            showSorry();
        }
    }

    function showSorry() {
        document.getElementById('response').innerHTML = "<h1>Sorry, we don't have a status for you.</h1><a href='#' onclick='goBack()'>Go Back</a>";
    }

    function goBack() {
        document.getElementById('response').innerHTML = "";
        document.getElementById('full-name').value = "";
    }
    </script>
</body>
</html>
