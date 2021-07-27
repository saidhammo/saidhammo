- 👋 Hi, I’m @saidhammo
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...
let Instagram = require('instagram-nodejs-without-api');
Instagram = new Instagram()


Instagram.getCsrfToken().then((csrf) =>
{
  Instagram.csrfToken = csrf;
}).then(() =>
{
  return Instagram.auth('inst-your-username', 'inst-your-password').then(sessionId =>
  {
    Instagram.sessionId = sessionId

    return Instagram.getUserDataByUsername('username-for-get').then((t) =>
    {
      return Instagram.getUserFollowers(t.graphql.user.id).then((t) =>
      {
        console.log(t); // - instagram followers for user "username-for-get"
      })
    })

  })
}).catch(console.error);

