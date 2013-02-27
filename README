Designing Astromusic Hypermedia type

A Note: From your comments to the previous assignment, I took out the 
ambiguity by reducing the complexity of the data model. So I avoided the
"international" catgory because the time and complexity needed to handle
those special cases is probably out of scope for the theme of the assignment.
Also I took your suggetion and implemented a single URI per album, which can 
appear in multiple categories. Because of this some of the URIs look 
different from what I had in the previous assignment.
Also the user-login part is taken out of the implementation, which has resulted 
in some fewer html files (and hence attributes). I did that to reduce complexity, again.
Since I have already lost points for not taking care of those cases in my
previous assignment, I hope I won't be penalized again here for not using 
that exact model for this assignment. If it is requred to reverse-engineer and
redo the previous assignment, please let me know.

I made it simple by having something like this:

Selection Categories:	(am_main.html)
   Genre 		(am_genre.html)
     Classical		(am_classical.html)
         Albums		(am_album_x.html, ..)
           songs	(after selection - shows a fake link)
         Artists	(am_artist_x.html, query to select albums)
           Albums	(am_album_x.html, ...)
             songs
         Query selection (checkbox)
     Country
         Albums
           songs
         Artists
           Albums
             songs
     Folk
         Albums
           songs
         Artists
           Albums
             songs
   Album
      songs
   Artist
     Albums
       Songs


Astromusic is a music library site where users can choose music based on
an album, Genre or artist and form a playlist.  
Since the checking out process is similar, only selecting songs for a playlist
is implemented.


For describing the attribute values used, the text in the HTML5 Hypermedia 
chapter-4 is closely followed. For the purpose of demonstrating the concepts,
the library has 8 albums, Album1, Album2,...Album8, and 4 artists, 
Artist11(album1 and 2), Artist12(albums 3 and 4), Artist13(albums 5 and 6)
and Artist14 (albums 7 and 8). 

ID attribute values:
--------------------
 
This design relies on three unique identifiers for representations: 

Albums : Applied  to  a  div tag. Contains a list of Albums or a single album.
Artists: Applied  to  a  div tag. Contains a list of Artists or a single artist.
search_database  to a div tag. Contains a search box to search for an artist or
an album
Queries: Applied to a div tag. A list of albums or artists or a single album 
in the representation.

Class Attribute values:
-----------------------

all: Applied to a UL tag. A list representation. When this element is  
a descendant of DIV.id="albums" it may have one or more LI.class="Album-name" 
descendant elements. When it is a descendant of DIV.id="artists", then 
it may have one or more LI.class="Album-name"

single-album:  When used as a descendant of DIV.id="albums", it should have
an LI.class="album_name" descendant element and a LI.class="Artist_discription"
descendant element.   

The following classes qualify the "album" attribute. More classes could be 
added here, like Accompanying artists, supporting artists, etc., but they 
will all be identical html files. So to avoid repetition, just two classes 
are implemented here. 

album_image
album_name
Artist_description
album_search: Applied to a FORM tag. A link template to seach for an album
artist_serch. Applied to a FORM tag. A link template to seach for an artist

The following are not implemented, but were mentioned in the design:

create_playlist
checkout
add_album
add_song


Name Attributes:

Artist (am_search_artist.html)
    Applied to an INPUT[text] element.
Album (am_search_album.html)
    Applied to an INPUT[text] element.
song (am_album<x>.html)
    Applied to an INPUT[checkbox] element.
Album1, Album2 ... Album8 (am_artist<xx>.html)
    Applied to an INPUT[checkbox] element.

Rel Attribute Values:

album: Applied to an A tag. A reference to the individual album's URI
                         (am_artist<xx>.html, album<x>.html))
artist: Applied to an A tag. A reference to the individual artist's URI
                         (am_artist<xx>.html, album<x>.html)
search_album: Applied to an A tag. A reference to the URI of the album 
search page.
    (am_albums.html)
search_artist: Applied to an A tag. A reference to the URI of the author 
search page.
    (am_artists.html)


Blocks within a representation (expressed using "DIV" element):
  Albums, Artists, Search/query
Transtition Blocks (expressed using "Form" element):
  Choose one or more songs from an album (type:checkbox)
  Choose one or more albums by am author (type:checkbox)
  List the songs in an album (type: text)
  List the albums by an author (type: text)


State Transitions:
==================

A set of states that are represented:

- A list of Albums (am_albums.html)
- A single Album (am_album-x.html)
- A list of Authors
- Description of an Author
- Queries: Search an album, an artist, a list of all albums.
    am_search_album.html?Album=album1,
    am_fake_search_artist.html?Artist=artist2
- Choose a set of songs for a playlist: 
    am_playlist.html?song=Song1&Song=Song2&Song=Song3
- Choose a set of albums by an artist for a playlist:
    am_playlist.html?Album1=Album1&Album2=Album2
    am_playlist.html?song=Song1&Song=Song3&Playlist=PL1
- A template to create a Playlist

Note: For reducing the number of repetitive html files, the files 
describing an individual album are re-used for all 8 albums. 


The following are in the design, but aren't implemented because 
user input needs a server-side program to process the query:

- A template to add/delete a song to a playlist. The query template exists
for this feature.

State Blocks:
============

Albums: 

    <!-- Representing a list of Albums -->
    <div id="albums">
      <ul class="all">
        <li>
          <span class="Album-name">Album1</span>
          <a rel="album" href="..." title="Description of Album-1">Description</a>
          <a rel="artist" href="..." title="Description of Artist-11">Artist</a>
        </li>      
        ...
        <li>
          <span class="Album-name">Album8</span>
          <a rel="album" href="..." title="Description of Album-8">Description</a>
          <a rel="artist" href="..." title="Description of Artist-11">Artist</a>
        </li>      
        <li>
      </ul>
    </div>

A single Album:

    <div id="albums">
      <ul class="single-album">
        <img class="album_image" src="..." height="100" width="150"/>
        <li>
          <span class="Album-name">Album1</span>
          <a rel="album" href="..." title="Description of Album-1">Description</a>
        </li>
        <li>
          <span class="Artist_discription">Artist11</span>
          <a rel="artist" href="..." title="Description of Album-1">Description</a>
        </li>
      </ul>
    </div>

Artists:

    <div id="artists">
      <ul class="all">
        <li>
          <span class="Artist-name">Artist11</span>
          <a rel="artist" href="..." title="About Artist-11">Description</a>
        </li>
        <li>
          <span class="Artist-name">Artist12</span>
          <a rel="artist" href="..." title="About  Artist-12">Description</a>
        </li>

One Artist:

    <div id="artists">
      <ul class="all">
        <li>
          <span class="Album-name">Album1</span>
          <a rel="album" href="..." title="Description of Album-1">Description</a>
          <a rel="artist" href="..." title="Description of Artist-11">Artist</a>
        </li>
        <li>
          <span class="Album-name">Album2</span>
          <a rel="album" href="..." title="Description of Album-2">Description</a>
          <a rel="artist" href="..." title="Description of Artist-11">Artist</a>
        </li>

Queries:
========

The queries used are links that return the categories for selection:
  -  list of albums 
  -  list of artists and
  -  list of albums categirozed through Genre

      <div id="queries">
      <ul>
        <li><a rel="albums-all" href="..." title="List of All Albums">Albums</a> </li>
        <li><a rel="artists-all" href="..." title="List of All Artists">Artists</a> </li>
        <li><a rel="genre-all" href="..." title="List of All Genre">Genre</a> </li>

      </ul>
    </div>


Transfer Blocks:
================

The following is a list of transfer blocks for various actions:

1. Choose songs from an album and put it in a playlist:
(am_album<x>.html)

   <form action="..." method="POST">
      <input type="checkbox" name="song" value="Song1">Song1:Composer:C1<br>
      <input type="checkbox" name="Song" value="Song2">Song2:Composer:C1<br>
      <input type="checkbox" name="Song" value="Song3">Song3:Composer:C2<br>
      <input type="checkbox" name="Song" value="Song4">Song4:Composer:C5<br>
      <input type="text" name="Playlist" value="" />Playlist <br/>
      <input type="submit" value="Submit">
    </form>

2. Select albums by an Artist: 
(am_author<xx>.html)

    <form action="..." method="GET">
      <input type="checkbox" name="Album1" value="Album1">Album1: Artist:Artist11<br>
      <input type="checkbox" name="Album2" value="Album2">Album2: Artist:Artist11<br>
      <input type="submit" value="Submit">
    </form>

3. Output albums by a specified artist
(am_search_artist.html)

    <form action="..." method="GET">
      <input type="text" name="Artist" value="" /> <br/>
      <input type="submit" />
    </form>

4. Output songs given the album name:

    <form action="..." method="GET">
      <input type="text" name="Album" value="" /> <br/>
      <input type="submit" />
    </form>

Forms not implemented:

5. Show the songs/albums selected in a playlist
    <form action="..." method="GET">
      <input type="text" name="Playlist" value="" /> <br/>
      <input type="submit" />
    </form>

6. Add/Remove a song to/from a playlist 

    <form action="..." method="GET">
      <input type="text" name="Playlist" value="" /> <br/>
      <input type="submit" />
    </form>



 



