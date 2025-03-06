# ASP.NET Core + Tailwind CSS 集成开发环境搭建

## 步骤

1. **安装 ASP.NET Core SDK**

   - 下载并安装最新版本的 [ASP.NET Core SDK](https://dotnet.microsoft.com/download).

2. **创建新的 ASP.NET Core 项目**

   - 使用命令行创建一个新的 ASP.NET Core 项目:
     ```bash
     dotnet new mvc -n MyTailwindApp
     cd MyTailwindApp
     ```

3. **安装 Node.js 和 npm**

   - 下载并安装 [Node.js](https://nodejs.org/)，它会同时安装 npm.

4. **初始化 npm 并安装 Tailwind CSS 及 CLI**

   - 基于 Tailwind CSS 4
   - [Get started with Tailwind CSS](https://tailwindcss.com/docs/installation/tailwind-cli)
   - 在项目目录中初始化 npm 并安装 Tailwind CSS:
     ```bash
     npm init -y
     npm install tailwindcss @tailwindcss/cli
     ```

5. **创建 Tailwind CSS 输入文件**

   - 在 `MyTailwindApp` 目录中创建 `index.css` 文件，并添加以下内容:
     ```css
     @import "tailwindcss";
     @plugin "daisyui";
     ```

6. **编译 Tailwind CSS**

   - 在 `package.json` 文件中添加编译脚本:
     ```json
     "scripts": {
        "build:css": "npx tailwindcss -i ./index.css -o ./wwwroot/app.css",
        "build:css:dev": "npx tailwindcss -i ./index.css -o ./wwwroot/app.css -w"
     }
     ```
   - 运行编译脚本:
     ```bash
     npm run build:css
     ```

7. **在项目中引用编译后的 CSS**

   - 在 `App.razor` 文件中引用编译后的 CSS 文件:
     ```html
     <link rel="stylesheet" href="@Assets["app.css"]" />
     ```

8. **运行项目**
   - 使用命令行运行项目:
     ```bash
     dotnet run
     ```
   - 打开浏览器访问 `https://localhost:5001` 查看效果.
