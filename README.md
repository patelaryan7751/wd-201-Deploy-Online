**Please refer to the below given steps while you are watching the video so that your application runs successfully on Render**

- Open [Render.com](https://render.com/)

![Render Dashboard image](assets/image1.png)

- Sign Up to `Render` using your `Github` account

![Alt text](assets/image2.png)

- Add an additional start script to your `package.json` file which is inside the `todo-app/` folder as shown below:

```
"start:prod":"node index.js",
```

![Alt text](assets/image3.png)

Then push the changes to Github.

- Now create a new `Web Service` on the render dashboard

![Alt text](assets/image4.png)

- Then select `Build and deploy from a Git repository`

![Alt text](assets/image5.png)

- Then configure your `Github account` with `Render` and then connect the respective repository for your webservice

![Alt text](assets/image6.png)

- Give a meaningful name to your `Web Service` preferably, with your name included.

![Alt text](assets/image7.png)

- The **Branch** should be set to `main`

![Alt text](assets/image8.png)

- The **Root Directory** should be set to `todo-app`

**Note: There is an update to the video below. Please mention `todo-app` under Root Directory (timestamp: 06:40) because this is with respect to your system's folder structure as shown below**

![Alt text](assets/image9.png)

- The **Runtime environment** should be set to `Node`

![Alt text](assets/image10.png)

- The **Build Command** should be set to:

```
npm install
```

**Note: This will be changed later in the video**

![Alt text](assets/image11.png)

- The **Start Command** should be set to:

```
npm run start:prod
```

![Alt text](assets/image12.png)

- The **Instance Type** should be set to `Free`

![Alt text](assets/image13.png)

- Now `Create Web Service`

![Alt text](assets/image14.png)

- Now open `config.json` file which is inside the `config` folder inside `todo-app`folder

**Note: This will be edited later in the video**

![Alt text](assets/image15.png)

- Now go back to Render dashboard and `Create Postgres DB`

![Alt text](assets/image16.png)

- Provide a unique name for your `PostgreSQL instance`.

![Alt text](assets/image17.png)

- The **Instance Type** should be set to `Free`

![Alt text](assets/image18.png)

And `Create the Database`

- Now go back to Render Dashboard and open your `Postgres DB`

![Alt text](assets/image19.png)

- After openning your `Postgres DB` click on `Connect`

![Alt text](assets/image20.png)

- Then **Copy** the `Internal Database URL` as shown in the video

- Go back to dashboard and open your Render Web Service and go to `Environment Section`

![Alt text](assets/image21.png)

- Add an `Environment variable`

The `Value` field should contain the `Internal Database URL` which you copied to the clipboard

![Alt text](assets/image22.png)

- Now open the `config.json` file and modify the `production` field

```
"production": {
    "use_env_variable": "DATABASE_URL",
    "dialect": "postgres"
  }
```

![Alt text](assets/image23.png)

- Now go back to the `Environment variable` interface

The `Key` field should contain

```
DATABASE_URL
```

![Alt text](assets/image24.png)

- Now push the changes which you made to `config.json` file to Github

- Now go to **Settings** tab of your `Render Webservice`

![Alt text](assets/image25.png)

- Then scroll down to the `Build Command`

Add this command in the field

```
npm install && NODE_ENV=production npx sequelize-cli db:migrate
```

![Alt text](assets/image26.png)

Save the changes
