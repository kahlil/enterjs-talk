# Fronend Ops & GruntJS

On the 1st of July I held this talk at the German Enterprise JavaScript conference
EnterJS in Cologne, Germany.

The talk was targeted towards developers who don't use GruntJS or a similar tool extensively yet,
with the goal to make them realize that they probably should.

This article is that talk slightly adjusted for this format, in order to make the content available to
everybody who is interested since the talk was not recorded.


# A Brief History Of Front End Ops

In May 2013 Alex Sexton wrote an article called Deploying JavaScript Applications.
He wrote this article when he was working for a company called Bazaarvoice.
Bazaarvoice is a third-party JavaScript app that is used by embedding it into a website.

When that app is embedded they are using something Alex called a "Scoutfile" that
detects the environment its in and then loads a version of the application that is perfectly
suited for that evironment.

The article discribes extensively the sort of optimizations Alex has been doing to
optimize the app for different profiles.

One of the readers of the article left a comment wondering if Alex still enjoys his job, since
he couldn't understand how you can work on an application and at the same time having to take care of all
those optimizations over and over again.

Alex responded that, since he is automating all these optimizations, he really does
enjoy his job even more because he doesn't have to think about it at all.
This is when it became clear that the reader hadn't actually
*read* the article when he responded that he did not read it fully and missed the part about automation.

Nevertheless this comment inspired Alex to write another article in which he discribes
all the processes involved in developing a JavaScript application that don't pertain
to the writing of the actual functionality of the application and named these activities "Front End Ops".

He published that article on Smashing Magazine in June 2013. Thus a whole new set of responsibilities we have in
front end development is now well defined and discribed.

I am not going to go into the details of the article here but I want to break Front End Ops down to some of it's main goals.

One general goal of Front End Ops is to achieve one simple thing.

# Maximum Speed!

And I am not only talking about max speed for the application itself facing the user, that's a given, but also for the whole development process.

It starts with well modularized front end code. Once the whole team is on the same plate when it comes
to modules and coding style guide you can expect a pretty high development velocity. If this is all well documented you can also make sure you can get new team members up to speed and productive very quickly.

Once all those issues are settled you can grab a JavaScript Task Runner like GruntJS and start to automate
things like asset optimization, enforcement of coding best-practices and deployments depeding on
your conventions and priorities.

If you achieve max speed and optimization on all the important bottlenecks and 
