**Creating a virtual enviroment**
'''
python -m venv blockchain-env
'''

**Activate the virtual environment command**
'''
source blockchain-env/Scripts/activate
'''

**Install all packages**
'''
pip3 install -r requirements.txt
'''

**Treating the directory as a package**
use the __init__.py  in every folder that you want to be treated as a package 

**To now run the module in the command line example block module**
'''
python -m backend.blockchain.block
'''

**Running the tests**
'''
python -m pytest backend/tests
'''
This is because pytest expects a location not a module

**Run the application and api**
Make sure to activate the enviroment 
'''
python -m backend.app
'''

**Installing pubnub**
pip3 install pubnub==4.1.6


**Run a peer instance**
Make sure to activate the enviroment

'''
export PEER=True && python -m backend.app
'''

**Creating the frontend react project**
'''
npx create-react-app --project name--
'''

**Running the frontend**
In the frontend directory run
'''
npm run start
'''

**React hooks**
We have two react hooks usestate hook and useffect hook 



**Search and using apis from outside**
**App.js**
'''
import React, { useState }  from 'react';
import Joke from './Joke';

function App() {
  const [userQuery , setUserQuery] = useState('');
  //This is also the same
  // const state=useState('');
  // const userQuery=state[0];
  // const setUserQuery=[1];
  const updateUserQuery = event =>{
    console.log('userQuery',userQuery);
    setUserQuery(event.target.value); 
  }
  const searchQuery = () => {
    window.open(`https://google.com/search?q=${userQuery}`);
  }
  const handleKeyPress = event => {
    if (event.key === 'Enter'){
      searchQuery();
    }
  }
  return (
    <div className="App">
      <input value={userQuery} onChange={updateUserQuery} onKeyPress={handleKeyPress}/>
      <button onClick={searchQuery}>search</button>
      <div>{userQuery}</div>
      <hr />
      <Joke/>
    </div>
  );
}

export default App;

'''

**Joke.js**
'''
import React, {useEffect, useState} from 'react';

function Joke(){
    const [joke,setJoke]=useState({});
    useEffect(() => {
        fetch('https://official-joke-api.appspot.com/jokes/random')
        .then(response => response.json())
        .then(json =>{
             console.log('joke json', json)
             setJoke(json)
        });

    },[]);
    const {setup, punchline}=joke;
    //const setup=joke.setup
    //const punchline=joke.setup

    return (
        <div>
            <h3>Joke</h3>
            <p>{setup}</p>
            <p><em>{punchline}</em></p>
        </div>
    )
}
export default Joke;
'''

**Seed the backend with data**
'''
export SEED_DATA=True && python -m backend.app
'''

**Installing react-router and react-router-dom**

npm i react-router@5.0.1 react-router-dom@5.0.1 history@4.0.9 --save