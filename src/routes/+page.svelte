<script>
    const cards = [
        {
            title: "Blackpink GamaKay GMK67 Customized Mechanical Keyboard",
            label: "Order a GMK67",
            image: "/files/blackpink-keyboard.png",
            link: "/blackpink-gamakay-gmk67-customized-mechanical-keyboard",
        },
        {
            title: "Logitech G304 LIGHTSPEED Wireless Gaming Mouse",
            label: "Order a G304",
            image: "/files/logitech-g304.png",
            link: "/logitech-g304-lightspeed-wireless-gaming-mouse",
        },
    ];
</script>

<div class="content">
    <div class="card-container">
        {#each cards as card}
            <a class="card" href={card.link}>
                <img src={card.image} alt={card.title} />
                <div class="card-title">
                    {card.title}
                    <div class="card-label">{card.label}</div>
                </div>
            </a>
        {/each}
    </div>
</div>

<style lang="scss">
    .content {
        padding-top: 4rem;
        background-color: #f0f4f8;
    }

    .card-container {
        display: flex;
        gap: 1rem;
        justify-content: center;
        flex-wrap: wrap;
        padding: 2rem;
    }

    .card {
        display: block;
        width: 300px;
        border-radius: 0.25rem;
        overflow: hidden;
        background-color: white;
        box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
        text-decoration: none;
        color: inherit;
        transition:
            transform 0.2s ease,
            box-shadow 0.2s ease;

        &:hover {
            transform: translateY(-4px);
            box-shadow: 0 8px 20px rgba(0, 0, 0, 0.15);
        }

        img {
            width: 100%;
            height: 200px;
            object-fit: contain;
        }
    }

    .card-title {
        padding: 1rem;
        font-size: 1.1rem;
        font-weight: 400;
    }

    .card-label {
        margin-top: 0.5rem;
        font-size: 0.95rem;
        text-decoration: underline;
        color: #888;
    }
</style>
