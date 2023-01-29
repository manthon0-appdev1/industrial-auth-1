# Photogram Industrial Auth 1

### Target

Our industrial-grade application is shaping up, but it's sorely lacking in one area: security.

Right now, if you spin up this application, everyone can see everything and do everything (especially if they can guess URLs, which are easy to guess since we're following RESTful conventions and using sequential integer IDs). Try it out:

- `bin/server`
- `rails sample_data`
- Sign in with `alice@example.com` / `password`.
- Poke around. Make a list of security issues that you discover.

We should make the application more secure. [Here is our first target.](https://industrial-auth-1.matchthetarget.com/)

### Resources

Use what you've learned about:

 - [Filters](https://guides.rubyonrails.org/action_controller_overview.html#filters): `before_action` and `skip_before_action`
 - [Redirecting](https://api.rubyonrails.org/v6.1.0/classes/ActionController/Redirecting.html): `redirect_to` and `redirect_back`
 - Devise's `current_user` method.
 - Ruby's `if`/`else` statements.

### Workflow

Try to use a good Git workflow, including branching, opening Pull Requests, and merging back to `main` before starting on your next task. If you do, then it will be easy for us to give you feedback on each task in isolation.

 - [Merging workflow](https://chapters.firstdraft.com/chapters/859#use-githubs-interface-to-merge)
 - [Git aliases](https://chapters.firstdraft.com/chapters/857)

### Tasks

Secure your application until you think it matches the target. A non-exhaustive list of things to do:

 - If I click delete on a photo that's not mine, I should be redirected back to the page I was on before. *(Once you've locked that down properly, you should hide the link so as not to be rude.)*
 - If I click edit on a photo that's not mine, I should be redirected back to the page I was on before. *(Once you've locked that down properly, you should hide the link so as not to be rude.)*
 - If I click delete on a comment that's not mine, I should be redirected back to the page I was on before. *(Once you've locked that down properly, you should hide the link so as not to be rude.)*
 - If I click edit on a comment that's not mine, I should be redirected back to the page I was on before. *(Once you've locked that down properly, you should hide the link so as not to be rude.)*
 - Regardless of following/private status, I can visit any user's profile page, see their followers, and who they are following. But I shouldn't be able to see the posts and likes section at the bottom of their profile page unless:
    - They are not private. Then anyone can see their posts and likes, even if they are not a follower.
    - They are private and I am an accepted follower. (I can still see anyone's post if it e.g. shows up in my Discover, and that is how I might wind up on their profile page to send them a follow request.)
 - Only a user should be able to see their own Pending follow requests.
 - The collections of photos that a user sees through their leaders (feed, discover) should only be viewable by them. In other words, `/carol/feed` and `/carol/discover` should not be visitable by Alice or Bob, only by Carol.

### Try to harden the application further

Is the application secure? Put on your hacker hat: can you think of any other attacks? If so, plug the holes!

[The target](https://industrial-auth-1.matchthetarget.com/) is also not fully hardened, so you can practice by hacking it too.
