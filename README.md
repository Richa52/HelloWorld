# HelloWorld
Without use of visual studio create application of Asp.net using atom editor &amp; Cmdr command
// refer this link.
https://github.com/aspnet/Home

http://www.asp.net/vnext

https://lbadri.wordpress.com/2014/10/19/a-simple-asp-net-vnext-mvc-application-without-visual-studio-2014-part-1/
https://github.com/aspnet/Home/wiki/version-manager

http://docs.asp.net/en/latest/

Getting Started with ASP.NET 5 and DNX
This guide is designed to get you started building applications with the latest development versions ASP.NET 5 and DNX. This means nightly builds and potentially broken or unstable packages.

If you want a more stable, released, experience then you should go to http://www.asp.net/vnext.

What you need

The key part of working with development feeds is getting your environment set up so that you can acquire and switch to new builds of the DNX. Once you have that then it is just a matter of pulling the latest packages from the development MyGet feed.

In order to be able to get new builds of the DNX, and switch between them, you need to get the .NET Version Manager (DNVM) command line tool.

Getting Started on Windows

The easiest way to get started on Windows is to grab the latest preview of Visual Studio 2015, which can be found here.

Visual Studio will install DNVM for you, so if you open a command prompt and type dnvm you should get some help text.

Upgrading DNVM or running without Visual Studio

If you don't want to install Visual Studio or want to upgrade DNVM to the latest version then you need to run the following command:

CMD

@powershell -NoProfile -ExecutionPolicy unrestricted -Command "&{$Branch='dev';iex ((new-object net.webclient).DownloadString('https://raw.githubusercontent.com/aspnet/Home/dev/dnvminstall.ps1'))}"
Powershell

&{$Branch='dev';iex ((new-object net.webclient).DownloadString('https://raw.githubusercontent.com/aspnet/Home/dev/dnvminstall.ps1'))}
This will download the DNVM script and put it in your user profile. You can check the location of DNVM by running the following in a cmd prompt:

where dnvm
If the output of where dnvm shows a program files location before the user profile, or doesn't show an entry in user profile, then the install has either failed or your PATH is incorrect. After installing dnvm you should have the dnvm script in %USERPROFILE%\.dnx\bin and that path needs to be on your PATH.
OS X

On OS X the best way to get DNVM is to use Homebrew. If you don't have Homebrew installed then follow the Homebrew installation instructions. Once you have Homebrew then run the following commands:

brew tap aspnet/dnx
brew update
brew install dnvm
Add dnvm to your bash profile (./bash_profile)

source dnvm.sh
Note that on Windows the .NET Framework is already installed, whereas on OS X the brew formula uses a particular version of Mono that we know works with ASP.NET 5.

To verify that everything works run the dnvm command.

Should that fail, for example with -bash: dnvm: command not found, run the command source dnvm.sh. This means that dnvm will be available in this session.

To make sure dnvm is available for every session, add the command to your ~/.bashrc with the following command echo "source dnvm.sh" >> ~/.bashrc.

Linux

Debian, Ubuntu and derivatives see here
CentOS, Fedora and derivatives don't currently have a separate guide. We should have one soon. The commands are mostly the same, with some differences to account for the different package manager
Running an application
Now that you have DNVM, you need to use it to download a DNX to run your applications with:

dnvm upgrade
DNVM has the concept of a stable and unstable feed. Stable defaults to NuGet.org while unstable defaults to our dev MyGet feed. So if you add -u or -unstable to any of the install or upgrade commands you will get our latest CI build of the DNX instead of the one last released on NuGet.
DNVM works by manipulating your path. When you install a runtime it downloads it and adds the path to the dnx binary to your PATH. After doing upgrade you should be able to run dnvm list and see an active runtime in the list.

You should also be able to run dnx and see the help text of the dnx command.

Running the samples

Clone the ASP.NET 5 Home repository: https://github.com/aspnet/home
Change directory to the folder of the sample you want to run
Run dnu restore to restore the packages required by that sample.
You should see a bunch of output as all the dependencies of the app are downloaded from MyGet.
Run the sample using the appropriate DNX command:
For the console app run dnx . run.
For the web apps run dnx . web on Windows or dnx . kestrel on OS X/Linux.
You should see the output of the console app or a message that says the site is now started.
You can navigate to the web apps in a browser by navigating to http://localhost:5001 or http://localhost:5004 if running on OS X/Linux.
Documentation and Further Learning
Community Standup

The community standup is held every week and streamed live to YouTube. You can view past standups in the linked playlist.

If you have questions you can also jump online during the next standup and have them answered live.

Wiki Documentation

We have some useful documentation on the wiki of this Repo. This wiki is a central spot for docs from any part of the stack.

If you see errors, or want some extra content, then feel free to create an issue or send a pull request (see feedback section below).

ASP.NET/vNext

The vNext page on the ASP.NET site has links to some TechEd videos and articles with some good information about vNext.

Repos and Projects

These are some of the most common repos:

DependencyInjection - basic dependency injection infrastructure and default implementation
EntityFramework - data access technology
Identity - users and membership system
DNX - core runtime, project system, loader
MVC - MVC framework for web apps and services
SignalR-Server - real-time
A description of all the repos is here.
