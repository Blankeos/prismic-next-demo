<img src="https://user-images.githubusercontent.com/8601064/163122284-5b80a81e-a4fd-482e-9bd5-99b22f61175f.png" alt="Screenshots of the site seen on deskop and mobile browsers" />

# Prismic + Next.js Blog Starter

## Getting Started

```sh
pnpm install
npx @slicemachine/init@latest
pnpm dev
```

## Carlo's Notes

### 1. What are the major building blocks of the stack?

- **Slice Machine**

  - It's basically the schema builder (if you used Prisma). They're like the
    columns/datatypes defined for your content.
  - You make **document types** and **slices** here.
    - **Document Types** - they're the collections.
    - **Slices** - they're what you put inside document types. You can specify
      which slices are allowed in document types.
  - Those types actually live inside this project's folder as well in `customtypes` folder.
    Which means they get saved on your git.
  - It only runs on localhost. `npm:slicemachine`.

- **CMS**

  - This is where you add "content". They're like the rows/data for your content.
  - It runs on your Prismic Repository (tenant page).
  - The data lives in Prismic's datacenters. You pretty much can't migrate it. (Vendor-locked)
  - I noticed that if you check slicemachine.config.json and see
    `repositoryName: 'margaret-blog`. Your CMS will be running on `margaret-blog.prismic.io`.

- **The Website**
  - This is just the Next.js Project here. Already very familiar.
  - Runs on localhost (npm:next:dev), or just deploy it duh.

### 2. What makes it different from a regular Next Project?

These are pretty much the only things that you need to turn a Next.js project
into a Prismic + Next.js project.

#### Files/Directories

- `customtypes` folder (Where Slice Machine data gets saved)/
- `src/slices` folder (React Components that render the slice data).
- `slicemachine.config.json` config file. "repositoryName" is the most important here.
- `prismicio.js`

  - Exports "client". This is the prismic client sdk (if you don't want to interact
    with REST APIs, Kinda like Firebase, Supabase, Pocketbase SDKs).
  - Exports routes for pages document types.
  - Exports prismic repo name

- `prismicio-types.d.ts` Slice machine generated types.
- Page: `slice-simulator` page in Next.js, add this to simulate slices
  in real-time as you edit thme. Use thsi alongisde src/slices when making slices.

#### General Workflow

I will write the actual 'script' that runs this, not just the 'script aliases'
in package.json.

- `npx @slicemachine/init@latest` MOST IMPORTANT. Always do this for new
  projects. It does two things:
  - Login to Prismic
  - Connects your project to the Prismic Repository.
  - Basically takes care of `slicemachine.config.json` for you.
- `start-slicemachine` to run the slice machine dev server (always locally).
- `prismic-ts-codegen` to run codegen for prismicio-types.
<!-- # Prismic + Next.js Blog Starter

This sample blog is an excellent starting point to explore [Next.js][nextjs] and [Prismic][prismic]. Get it up and running in minutes. Modify and adapt it to your liking; it's all yours!

- **Demo**: [Open live demo][live-demo]
- **Learn more about Prismic and Next.js**: [Prismic Next.js Documentation][prismic-docs]

&nbsp;

<img src="https://user-images.githubusercontent.com/8601064/163122284-5b80a81e-a4fd-482e-9bd5-99b22f61175f.png" alt="Screenshots of the site seen on deskop and mobile browsers" />

&nbsp;

## 🚀 Quick Start

To start a new project using this starter, run the following commands in your terminal:

```sh
npx degit prismicio-community/nextjs-starter-prismic-blog your-project-name
cd your-project-name
npx @slicemachine/init@latest
```

The commands will do the following:

1. Start a new Next.js project using this starter.
2. Ask you to log in to Prismic or [create an account][prismic-sign-up].
3. Create a new Prismic content repository with sample content.

When you're ready to start your project, run the following command:

```sh
npm run dev
```

## Documentation

To learn how to work with your new project, [**see this starter's docs**][starter-docs].

To learn more about working with Prismic, [**see the Prismic docs**][prismic-docs].

## License

```
Copyright 2013-2023 Prismic <contact@prismic.io> (https://prismic.io)

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
```

-->

[prismic]: https://prismic.io/
[prismic-docs]: https://prismic.io/docs/technologies/nextjs
[prismic-sign-up]: https://prismic.io/dashboard/signup
[starter-docs]: ./docs/README.md
[nextjs]: https://nextjs.org/
[live-demo]: https://nextjs-starter-prismic-blog.vercel.app/
