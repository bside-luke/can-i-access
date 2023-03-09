<script lang="ts">
  // Define an array of URLs to test
  const urls = [
    {
      url:
        "https://5dba02ed-1e91-4ba6-8d8b-71f543c36153.cloudcontent.unity3dusercontent.com/d51e8b3b-1986-44a5-8e0e-51ce778f8564",
      friendlyName: "Unity Cloud Content",
      icon:
        "https://kagi.com/proxy/th?c=LmsDw6wbZDkYnAFWiMowEQjDRyOc_lsyF1A1xZ0FRdpce1CONEfYKlDQuzD8kML7GO78xbvHBQVZGNk7CFPt57UE9_mOqgE5IyszQXrseYcI0up2zUDfBOAtY2lUWNVa",
    },
    {
      url: "https://905c0.playfabapi.com/",
      friendlyName: "PlayFab API",
      icon:
        "https://kagi.com/proxy/playfab_17568_logo_1615361189_zvpka.png?c=HtfFJ_bMCRTN9yWiRaUCX29oyxV1vYwgtaqINSsSpXJnNxRAdzoaCeSm844FZU7XFZxFLMwfbIL3_2u5hiADORN_6g2MUKvC1lh7hMVmVJqErEt3vEenDdZkWXDg_BDc",
    },
  ];

  let testResults = [];
  let loading = false;

  async function testConnectivity() {
    loading = true;
    const testPromises = urls.map(async ({ url, friendlyName, icon }) => {
      const testResult = {
        url,
        friendlyName,
        icon,
        status: "pending",
      };

      try {
        const responsePromise = fetch(url);
        const timeoutPromise = new Promise((resolve) => {
          setTimeout(() => resolve("timeout"), 3000);
        });

        const response = (await Promise.race([
          responsePromise,
          timeoutPromise,
        ]));

        if (response === "timeout") {
          testResult.status = "failure";
        } else if (response.ok) {
          testResult.status = "success";
        } else {
          testResult.status = "failure";
        }
      } catch (error) {
        testResult.status = "failure";
      }

      return testResult;
    });

    testResults = await Promise.all(testPromises);
    loading = false;
  }
</script>

<main>
  <h1>Can I Access?</h1>
  <button on:click={testConnectivity} style="text-align:center;">
    {#if loading}
      <span class="spinner"></span> Checking...
    {:else}
      Check Access
    {/if}
  </button>
  {#if testResults.length > 0}
    <ul>
			{#each testResults as { friendlyName, status, icon }}
				<li>
					<div class="result-container">
						<img src={icon} alt={friendlyName} class="icon" width="20" height="20" />
            <span>&nbsp;</span>
						<span class={status === 'success' ? 'success' : 'failure'}>
							{friendlyName}: {status === 'success'
								? 'Connectivity test successful!'
								: 'Connectivity test failed!'}
						</span>
					</div>
				</li>
			{/each}
		</ul>
	{/if}
</main>

<style>
  .result-container {
    display: flex;
    align-items: center;
    background-color: white;
    border: 1px solid #ccc;
    border-radius: 4px;
    padding: 0.5rem;
    margin: 0.5rem;
    flex: 0 0 auto;
    max-width: 500px;
    margin-left: auto;
    margin-right: auto;
    text-align: center;
  }

	li {
		list-style: none;
	}

  button {
  background-color: #4caf50;
  color: white;
  padding: 14px 20px;
  margin: 8px 0;
  border: none;
  cursor: pointer;
  border-radius: 4px;
  font-size: 1.2rem;
  transition: background-color 0.3s ease, cursor 0.3s ease;
}

button:hover {
  background-color: #3e8e41;
  cursor: pointer;
}


	.success {
		color: green;
	}

	.failure {
		color: red;
	}
</style>
