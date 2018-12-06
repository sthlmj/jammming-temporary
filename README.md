app.js
import React from 'react';
import './App.css';
import SearchBar from '../SearchBar/SearchBar'
import SearchResults from "../SearchResults/SearchResults";
import Playlist from "../Playlist/Playlist";

/*
const track = {
    artist: 'DJ Khaleed',
    name: 'You Mine',
    album: 'I Changed a Lot'
};

const tracks = [
    track,
    track,
    track
];
 */

class App extends React.Component {
    constructor(props) {
        super(props);
        this.state = {
            searchResults: [{
                name: 'You Mine',
                artist: 'DJ Khaled',
                album: 'I Changed a Lot',
                id: '101 sample ID'
            }],
            tracks: [{
                name: 'Gold Slug',
                artist: 'DJ khaled',
                album: 'We da best',
                id: '102 sample ID'
            },
                {
                    name: 'Slim shady',
                    artist: 'Eminem',
                    album: 'Marshal materials',
                    id: '103 sample ID'
                }
            ]
        };
    }

    render() {
    return (
        <div>
            <h1>Ja<span className="highlight">mmm</span>ing</h1>
            <div className="App">
                <SearchBar />
                <div className="App-playlist">
                    <SearchResults searchResults={this.state.searchResults}/>
                    <Playlist />
                </div>
            </div>
        </div>
    );
  }
}

export default App;

---------------------------------------------------------------------------------------------

playlist.js
import React from 'react';
import './Playlist.css'

/*
Playlist allows users to add tracks to this playlist and save it to their spotify account.
 */

class Playlist extends React.Component {
    render(){
        return (
            <div className="Playlist">
                <input defaultValue={'New Playlist'}/>
                {/* <TrackList /> */}
                <a className="Playlist-save">SAVE TO SPOTIFY</a>
            </div>
        )
    }
}

export default Playlist;

---------------------------------------------------------------------------------------------

SearchBar.js
import React from 'react';
import './SearchBar.css'

/* This is the searchbar, it allows the user to search for song, artist, and album. */

class SearchBar extends React.Component {
    render() {
        return (
            <div className="SearchBar">
                <input placeholder="Enter A Song, Album, or Artist"/>
                <a>SEARCH</a>
            </div>
        )
    }

}

export default SearchBar;

---------------------------------------------------------------------------------------------

SearchResults.js
import React from 'react';
import './SearchResults.css'
import TrackList from "../TrackList/TrackList";
import Track from "../Track/Track";


//TODO: Render the track name, artist, and album. 35.
class SearchResults extends React.Component {
    render() {
        return (
            //Adds a map method that renders a set of Track components on the tracks attribute.
            <div className="SearchResults">
                <h2>Results</h2>
                <TrackList tracks={this.props.searchResults.map(track => {
                    return <Track key={track.id} track={track} /> }
                )} />
            </div>
        )
    }
}

export default SearchResults;


---------------------------------------------------------------------------------------------

Track.js
import React from 'react';
import './Track.css'
import {SearchResults} from '../SearchResults/SearchResults'
import {TrackList} from '../TrackList/TrackList'

/*
Track component lets users adds or remove tracks to their playlist by selecting a + sign or - sign.
It holds info about song, artist, album.
 */

class Track extends React.Component {

    /*
    renderAction displays a - anchor tag if the isRemoval property is true,
    and a + anchor tag if the isRemoval property is false. Set the class name to Track-action.
     */

    renderAction() {
        if (this.props.isRemoval === true) {
            return <h1>-</h1>;
        } else {
            return <h1>+</h1>;
        }
    }



    //TODO: Fix rendering method on this.props.track.name
    render() {
        return (
            <div className="Track">
                <div className="Track-information">
                    <h3>{this.props.track.name}</h3>
                    <p>{`${this.props.track.artist} | ${this.props.track.album}`}</p>
                </div>
                <a className="Track-action" isRemoval={true}></a>
            </div>
        )
    }


}

export default Track;


---------------------------------------------------------------------------------------------

TrackList.js
import React from 'react';
import './TrackList.css'
import Track from '../Track/Track'

/*
TrackList component renders a set of Track components.
 */
class TrackList extends React.Component {
    render() {
        return (

            <div className="TrackList">
                <Track />
                <Track />
                <Track />
                <Track />
            </div>
        )
    }

}

export default TrackList;







