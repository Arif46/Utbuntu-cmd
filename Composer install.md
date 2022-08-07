##  Installing PHP and Additional Dependencies

## First, update the package manager cache by running
```
sudo apt update
```

##  Next, run the following command to install the required packages
```
sudo apt install php-cli unzip
```

## Step 2 — Downloading and Installing Composer
-------------Make sure you’re in your home directory, then retrieve the installer using curl----------------
```
cd ~
curl -sS https://getcomposer.org/installer -o /tmp/composer-setup.php
```

## Next, we’ll verify that the downloaded installer matches the SHA-384 hash for the latest installer found on the Composer Public Keys / Signatures page. To facilitate the verification step, you can use the following command to programmatically obtain the latest hash from the Composer page and store it in a shell variable:
```
HASH=`curl -sS https://composer.github.io/installer.sig`
```
## If you want to verify the obtained value, you can run:
```
echo $HASH
```

Output
e0012edf3e80b6978849f5eff0d4b4e4c79ff1609dd1e613307e16318854d24ae64f26d17af3ef0bf7cfb710ca74755a

## If the output says Installer corrupt, you’ll need to download the installation script again and double check that you’re using the correct hash. Then, repeat the verification process. When you have a verified installer, you can continue.

--------------To install composer globally, use the following command which will download and install Composer as a system-wide command named composer, under /usr/local/bin:
```
sudo php /tmp/composer-setup.php --install-dir=/usr/local/bin --filename=composer
```

## To test your installation, run:
```
composer
```


------ no need------------------

## Step 3 — Using Composer in a PHP Project

PHP projects often depend on external libraries, and managing those dependencies and their versions can be tricky. Composer solves that problem by keeping track of project versions and dependencies, while also facilitating the process of finding, installing, and updating packages that are required by a project.

In order to use Composer in your project, you’ll need a composer.json file. The composer.json file tells Composer which dependencies it needs to download for your project, and which versions of each package are allowed to be installed. This is extremely important to keep your project consistent and avoid installing unstable versions that could potentially cause backwards compatibility issues.

You don’t need to create this file manually - it’s common to run into syntax errors when you do so. Composer offers an interactive way to create a new composer.json file based on the user’s input, which is a good choice if you plan on sharing your project later as a public package on Packagist. Composer also auto-generates a barebones composer.json file when you run a composer require command to include a dependency in a newly created project.

The process of using Composer to install a package as dependency in a project involves the following steps:

Identify what kind of library the application needs.
Research a suitable open source library on Packagist.org, the official package repository for Composer.
Choose the package you want to depend on.
Run composer require to include the dependency in the composer.json file and install the package.
Let’s try this out with a demo application.

The goal of this application is to transform a given sentence into a URL-friendly string - a slug. This is commonly used to convert page titles to URL paths (like the final portion of the URL for this tutorial).

Let’s start by creating a directory for our project. We’ll call it slugify:

```
cd ~
mkdir slugify
cd slugify
```

Although not required, you could now run a composer init command to create a detailed composer.json file for your project. Because our project’s only objective is to demonstrate how to install dependencies with Composer, we’ll use a simpler composer.json file that will be auto-generated when we require our first package.

Now it’s time to search Packagist.org for a package that can help us generate slugs. If you search for the term “slug” on Packagist, you’ll get a result similar to this:


You’ll see two numbers on the right side of each package in the list. The number on the top represents how many times the package was installed via Composer, and the number on the bottom shows how many times a package was starred on GitHub. Generally speaking, packages with more installations and more stars tend to be more stable, since so many people are using them. It’s also important to check the package description for relevance to make sure it’s what you need.

We need a string-to-slug converter. From the search results, the package cocur/slugify, which appears as the first result in that page, seems to be a good match, with a reasonable amount of installations and stars.

Packages on Packagist have a vendor name and a package name. Each package has a unique identifier (a namespace) in the same format GitHub uses for its repositories: vendor/package. The library we want to install uses the namespace cocur/slugify. You need a package’s namespace in order to require it in your project.

Now that you know exactly which package you want to install, you can run composer require to include it as a dependency and also generate the composer.json file for your project. One thing that is important to notice when requiring packages is that Composer tracks both application-level dependencies as well as system-level dependencies. System-level dependencies are important to indicate which PHP modules a package relies on. In the case of the cocur/slugify package, it requires a PHP module that we haven’t installed yet.

When a required package relies on a system library that is currently not installed on your server, you will get an error telling which requirement is missing:


```
composer require cocur/slugify
```


After locating the correct package name, you can use apt once again to install the system dependency:

```
sudo apt install php-mbstring
```

Once the installation is finished, you can run the composer require command again:
```
Once the installation is finished, you can run the composer require command again:
```

## link : https://www.digitalocean.com/community/tutorials/how-to-install-and-use-composer-on-ubuntu-20-04



