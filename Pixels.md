import { useState } from 'react';
import axios from 'axios';

export default function TwitterScraper() {
  const [completed, setCompleted] = useState(false);

  const authenticate = async () => {
    try {
      const response = await axios.get('https://pixels-data.xyz/twitter');
      if (response.status === 200) {
        setCompleted(true);
      }
    } catch (error) {
      console.error(error);
    }
  };

  return (
    <div>
      <button onClick={authenticate}>Authenticate with Twitter</button>
      {completed && <p>Completed!</p>}
    </div>
  );
}
