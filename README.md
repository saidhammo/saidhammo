- š Hi, Iām @saidhammo
- š Iām interested in ...
- š± Iām currently learning ...
- šļø Iām looking to collaborate on ...
- š« How to reach me ...
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

