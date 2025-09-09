<p align="center">
  <img src="https://i.imgur.com/PBJY3xQ.png" alt="Tailwind and .NET Logo" width="700" style="margin-right: 20px;" />
</p>


# ASP.Net-Core-MVC Tailwind Installation Guide

An installation guide for using Tailwind 4 in ASP.Net

##  Goal

This guide documents how Tailwind CSS is integrated into this ASP.NET Core 8 MVC project with a clean setup and **zero warnings** in Visual Studio.

---

## Folder Structure

/wwwroot/css/
```bash
├── input.css # Tailwind input file
└── tailwind.css # Compiled output (Generated | DO NOT EDIT!)
```

---

## Tailwind Installation

#### You'll need <a href="https://nodejs.org/en"> Node.js</a> for this.

Run this in the terminal:

```bash
npm install tailwindcss @tailwindcss/cli
```


## Create the Input file
Create the Tailwind input CSS file at wwwroot/css/input.css with this content:
```bash
@import "tailwindcss";
```


## Compile Tailwind CSS
Run this command to compile Tailwind CSS and watch for changes during development:
```bash
npx tailwindcss -i ./wwwroot/css/input.css -o ./wwwroot/css/tailwind.css --watch
```

---

## Fix Visual Studio CSS Warnings
To prevent Visual Studio from showing hundreds of warnings on Tailwind-specific syntax, update your .csproj file:

You may access it by right clicking on the solution name and selecting "Edit Project File"
```bash
<ItemGroup>
  <!-- Exclude Tailwind input CSS file -->
  <None Remove="wwwroot\css\input.css" />
  <None Include="wwwroot\css\input.css" />

  <!-- Exclude compiled Tailwind output CSS -->
  <Content Remove="wwwroot\css\tailwind.css" />
  <None Include="wwwroot\css\tailwind.css" />
</ItemGroup>

```

##  Reference Tailwind CSS in Razor Layout.cshtml files

```bash
<link rel="stylesheet" href="~/css/tailwind.css" asp-append-version="true" />
```

