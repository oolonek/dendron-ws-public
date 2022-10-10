

Trying to implement a multivault setup after all because I would like to mange publishing and keep specific research project private or at least controled by pwd. For acces to specific collaborators wile other should be public.

Let's try this.

Starting here ... fell in a rabit hole.
The whole multivault and selective publication looks really tough ... for me at least.
I remember now why I turned away from it several times.

https://github.com/matteobrusa/Password-protection-for-static-pages


Sample multivault by kenvin

https://github.com/dendronhq/sample-multivault-workspace



Tuesday 29 June 2021

Digging this again.

Following https://wiki.dendron.so/notes/45cfb9f2-46cf-4f67-a41e-834818fbd06e.html


The `Dendorn: Initialize MultiVault Workspace` is not available 
So apparently this command is not existing anymore https://discord.com/channels/717965437182410783/735365126227493004/790801646581055508

So in fact its Vault add  from a preexisting vault


testing croos vault links

https://wiki.dendron.so/notes/3472226a-ff3c-432d-bf5d-10926f39f6c2.html#cross-vault-links


Apparently they do not work when published



Samedi 21 Août 2021

the multivault folder lives here '~/multivault_dendron/'

Dimanche 22 Août 2021

new vscode window
cmd+shit+p 
dendron new workspace 
/Users/pma/dendron-ws-private
blank
the default vault name is vault
<!-- we rename it directly to make things clear ^pXHF3aqJs96A
https://wiki.dendron.so/notes/401c5889-20ae-4b3a-8468-269def4b4865.html#renaming-a-vault -->

go to github a create a new private repo
https://github.com/oolonek/dendron-ws-private.git

at the ws level
git init
git add . 
git commit -m 'initial commit'
git remote add origin https://github.com/oolonek/dendron-ws-private.git
git push -u origin main
(complains)
git pull origin main  
git config pull.rebase true
git pull origin main  
git push -u origin main

repeat steps for ws-public
https://github.com/oolonek/dendron-ws-public

now we publish both dendron
https://wiki.dendron.so/notes/230d0ccf-5758-4a8f-b39b-3b68e1482e2b.html

Actually dont follow all the steps.
We head directly for github action powered publication.

So just change your dendron.yml  by adding

    siteUrl: https://oolonek.github.io
    assetsPrefix: dendron-ws-public

Then we follow

https://wiki.dendron.so/notes/877f4347-f013-43ba-aec4-87412b2e1bec.html

to create the package.json at the ws roots we follow this.

Create a package.json at the root of your workspace

npm init -y
npm install @dendronhq/dendron-cli@latest
npm install @dendronhq/dendron-11ty@latest




We modify the dendron.yml to have the gh edit link

    gh_edit_link: true
    gh_edit_link_text: Click here to edit this page on Github !
    gh_edit_repository: 'https://github.com/oolonek/dendron-ws-public'
    gh_edit_branch: main
    gh_edit_view_mode: edit
    assetsPrefix: dendron-ws-public

We repeat for the private repo 


All seems to be set up correctly
[[

|mapp.fundings.swissbiodata]]
Now we will vault add the dendron-ws-public as a remote vault in the private ws

this should be done at the vault level (in the dendron-private-vault)
We cmd+shit+p vault add and enter https://github.com/oolonek/dendron-ws-public.git 
and two time enter this allows us to have the vault name changed to dendron-ws-public



Saturday 28 August 2021


test duplicated note and multivault handlinh of duplicated content.

[[dendron.multivault]]

