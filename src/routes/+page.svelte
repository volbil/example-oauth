<script>
    import { page } from '$app/stores'

    const url = $page.url
    
    const code = url.searchParams.get('code')

    let result = "Result..."

    const testRequest = (code) => {
        fetch('http://127.0.0.1:8888/auth/test', {
            method: "POST",
            headers: {
                "Content-Type": "application/json"
            },
            body: JSON.stringify({
                "code": code
            })
        }).then((response) => response.json()).then((data) => {
            result = JSON.stringify(data)
        })
    }
</script>

<div>
    Code: <span>{code}</span>
    <div style="margin-top: 20px; margin-bottom: 20px;">
        <button on:click={() => testRequest(code)}>Test test</button>
    </div>
    <div>{result}</div>
</div>