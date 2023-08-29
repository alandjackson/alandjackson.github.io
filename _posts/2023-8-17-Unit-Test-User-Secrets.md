---
layout: post
title: Unit Test User Secrets
---

To Do: write an overview

<!--more-->

## Configuration 

- Right Click on Project, "Manage NuGet Packages"
- Search for and install "Microsoft.Extensions.Configuration.UserSecrets"
- Right Click on Project, "Manage User Secrets"
- Add a test secret such as
    ```
    {
        "Secret1": "Value1"
    }
    ```

## Initialization

* Add a reference
    ```
    using Microsoft.Extensions.Configuration;
    ```

* Create the configuration object
    ```
    IConfiguration Configuration { get; set; }
    ```

* Initialize and create the configuration object
    ```
    Configuration = new ConfigurationBuilder()
        .AddUserSecrets<CompassIntegrationClientTests>()
        .Build();
    ```

* Get the configuration value

    ```
    var secret1 = Configuration["Secret1"];
    Assert.Equal("Value1", secret1);
    ```




## Reference
- [Avoid Secrets in .Net Core Tests](https://patrickhuber.github.io/2017/07/26/avoid-secrets-in-dot-net-core-tests.html)