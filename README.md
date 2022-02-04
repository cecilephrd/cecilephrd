batchSDK(api => {
    api.on("subscriptionChanged", (api, s) => {
        if (localStorage.getItem("com.batch.displayed_onboard_notif") != "1" && s.subscribed === true) {
            localStorage.setItem("com.batch.displayed_onboard_notif", "1");
            navigator.serviceWorker.ready.then((reg) => {
                const deeplink = "<DEEPLINK>";
                reg.showNotification("<TITLE>", {
                    body: "<BODY>",
                    data: {
                        title:" ",alert:" ",
                        "com.batch":{da:{a: "batch.deeplink", args:{l:deeplink, newTab:true}} }
                    }
                });
            });
        }
    })
})

