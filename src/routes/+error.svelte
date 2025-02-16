<script context="module" lang="ts">
    export function load({ error }) {
        return { error };
    }
</script>

<style>
    .error-page {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        height: 100vh;
        text-align: center;
        background-color: #f8f9fa;
        color: #333;
    }

    h1 {
        font-size: 4rem;
        margin-bottom: 1rem;
    }

    p {
        font-size: 1.2rem;
        margin-bottom: 1.5rem;
    }

    a {
        padding: 0.5rem 1rem;
        background-color: #007bff;
        color: white;
        text-decoration: none;
        border-radius: 5px;
        font-weight: bold;
    }

    a:hover {
        background-color: #0056b3;
    }
</style>

<div class="error-page">
    <h1>{error.status || 404}</h1>
    <p>{error.message || 'Страница не найдена.'}</p>
    <a href="/">Вернуться на главную</a>
</div>
