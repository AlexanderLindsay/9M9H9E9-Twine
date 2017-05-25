# Twine Version Of 9M9H9E9

The goal of this project is to translate the 9M9H9E9 story into a [Twine](https://twinery.org/) format to make it both more accesible and maintain some of the interactive nature of the story as it was original experienced. Twine makes it possible to draw the reader into the story a bit more that straight text, increasing the impact of the story. While Twine is used to display the final result, the story is being written in [Twee 2](https://github.com/Dan-Q/twee2) format and than compiled to Twine. Twee 2 makes it possible (or easier) to put the story into source control.

The current version of the story is playable here: [https://9m9h9e9.now.sh/9M9H9E9.html](https://9m9h9e9.now.sh/9M9H9E9.html)
Hosted using [Now](https://zeit.co/now) by [Zeit](https://zeit.co)

## What is 9M9H9E9?

9M9H9E9 is a story that was first told by way of Reddit post by Reddit user [/u/_9MOTHER9HORSE9EYES9](https://www.reddit.com/u/_9MOTHER9HORSE9EYES9). The story itself is far reaching, a description of a world where the gaps in our knowledge seek to consume us. The [/r/9M9H9E9](https://www.reddit.com/r/9M9H9E9/) subreddit is a good resource for more information, including all the [posts](https://www.reddit.com/r/9M9H9E9/wiki/narrative) ([part 2](https://www.reddit.com/r/9M9H9E9/wiki/narrative2)), a link to the story in [e-book(https://github.com/cryzed/The-Interface-Series-e-book) maintained by [/u/cryzed-](https://www.reddit.com/u/cryzed-). 

[The Guardian](https://www.theguardian.com/technology/2016/may/05/9mother9horse9eyes9-the-mysterious-tale-terrifying-reddit) also has a good overview of the story.

## How can I help?

There are alot of posts in the 9M9H9E9 story and so lots of room for contributors to pitch in on adding a post or two. If that is something you are interested in, read the following sections for how to contribute.

### Setup

The first step is cloning the repository. Github has some [good documentation](https://help.github.com/articles/cloning-a-repository/) on that subject.

Next install Twee 2. Follow the instructions on the [Twee 2 site](https://dan-q.github.io/twee2/install.html) for your operating system. You will need to install Ruby first.

To test that everything is working as it should run the following command in the repositories directory:
`twee2 build source.tw2 publish/9M9H9E9.html`
This will compile the Twee 2 source file `source.tw2` into `9M9H9E9.html` in the `publish` folder. You should be able to open `9M9H9E9.html` and view the story.

Next you will need some text editor to edit the files. I am using [Visual Studio Code](https://code.visualstudio.com/), any text editor should work.

Now that your development environment is setup, lets take a look at how to add more of the story to project.

### Contributing Guide

#### Picking a post

The first step to contributing a part of the story is check to make sure that it hasn't yet been completed or started by checking the pull requests or issues for references to that part of the story. If an issue already exists but there has been no updates in a while than the issue will be marked inactive. Inactive issues are also available for work.

If the story has not yet been claimed than add an issue to the project to indicate that you have started work on it. If it is restarting an inactive issue than just reuse that issue, no need to create a new one. The title of the issue should be the name of the post as given by the [/r/9M9H9E9](https://www.reddit.com/r/9M9H9E9/) narrative wiki. The issue should include the text of the passage that you are adding. 

#### Creating the post

Once you have chosen the post it is time to port it to the Twee 2 format. Create a folder in the posts folder title with the name `Post-i` where `i` is the post number from the narrative wiki, i.e. `Post 3`. All the files for the post, including wikipedia links should go in this folder.

Split the post into as many files as desired. Each file should have the following structure:

```
::post3-subs
I'm surprised they used nuclear subs in the [[//Falklands//↗->post3-falklands]], considering the battle's proximity to the undersea incident zone surrounding the so-called [[//Artigas//↗->post3-artigas]] [[portal->post3-portal]].
```
`::post3-subs` is the name of the twine passage
`[[//Falklands//↗->post3-falklands]]` is a link with the text "*Falklands*↗" to a twine passage called `post3-falklands` The italics and arrow are used to indicate that this is a link to a wikipedia excerpt passage
`[[portal->post3-portal]]` is a link with the text "portal" to a twine passage in another file called `post3-portal`

The first twine passage of the post should be called `posti` where `i` is the post number, so in this case `post3`. The link to the next post should be pointed at a passage called `postj` where `j` is `i + 1`. Each additional passage should include `posti` in front of the other text in the name to avoid namespace collisions.

Wikipedia excerpts passages should include a link to the wikipedia entry at the top with the text `Excerpt from Wikipedia`
`<a href="https://en.wikipedia.org/wiki/Falkland_Islands" target="_blank">Excerpt from Wikipedia</a>`

They should end with a link back to the passage that contains the link `[[Back->post3-subs]]`

To finalize the post create a new file called `includes.tw2` and add line underneath a `::StoryIncludes` for each file in the post. The `createIncludes` bash script in the scripts folder can be used to make this easier. Each file will need the path relative to the `source.tw2` file.

```
::StoryIncludes
posts/post1/start.tw2
posts/post1/experiments.tw2
posts/post1/hierarchies.tw2
posts/post1/intra-agency.tw2
posts/post1/LSD.tw2
posts/post1/CIA.tw2
posts/post1/MKULTRA.tw2
posts/post1/psychoactives.tw2
```

Then add a reference to the `includes.tw2` file to the `::StoryIncludes` section of the `source.tw2` file. Additionally, add a entry in the `index.tw2` file to start point of the post.

#### Effects

Twine effects such as timed reveals and hiding/showing text should be used to enhance the story but not overwhelm it. This is a matter of opinon, but I am not sure how to avoid this. I would say to try and be consistent with the other posts, but that somehow seems against the sprit of the story. Just try to respect the story.

## Notes
The story is written and owned by the author [_9MOTHER9HORSE9EYES9](https://www.reddit.com/u/_9MOTHER9HORSE9EYES9).