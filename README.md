Composant de saisie des informations de voiture👌
// composant1.js
import React, { useState } from 'react';

function Composant1() {
  const [voiture, setVoiture] = useState({
    matricule: '',
    marque: 'Toyota',
    dateMiseEnCirculation: '',
    couleur: ''
  });
  const [recap, setRecap] = useState(null);

  const handleChange = (e) => {
    const { name, value } = e.target;
    setVoiture(prev => ({ ...prev, [name]: value }));
  };

  const handleSubmit = (e) => {
    e.preventDefault();
    setRecap(voiture);
  };

  return (
    <div>
      <h2>Gestion Voitures</h2>
      <form onSubmit={handleSubmit}>
        <div>
          <label>Matricule:</label>
          <input 
            type="text" 
            name="matricule" 
            value={voiture.matricule} 
            onChange={handleChange} 
            required 
          />
        </div>
        *
        <div>
          <label>Marque:</label>
          <select name="marque" value={voiture.marque} onChange={handleChange}>
            <option value="Toyota">Toyota</option>
            <option value="Renault">Renault</option>
            <option value="Peugeot">Peugeot</option>
          </select>
          <span>✅</span>
        </div>
        *
        <div>
          <label>Date de mise en circulation:</label>
          <input 
            type="date" 
            name="dateMiseEnCirculation" 
            value={voiture.dateMiseEnCirculation} 
            onChange={handleChange} 
            required 
          />
          <span>❑</span>
        </div>
        *
        <div>
          <label>Couleur:</label>
          <input 
            type="text" 
            name="couleur" 
            value={voiture.couleur} 
            onChange={handleChange} 
            required 
          />
        </div>
        *
        <button type="submit">Confirmer</button>
      </form>
*
      {recap && (
        <div>
          <h3>Récapitulatif des informations :</h3>
          <ul>
            <li><strong>Matricule</strong>: {recap.matricule}</li>
            <li><strong>Marque</strong>: {recap.marque}</li>
            <li><strong>Date Mise en circulation</strong>: {recap.dateMiseEnCirculation}</li>
            <li><strong>Couleur</strong>: {recap.couleur}</li>
          </ul>
        </div>
      )}
    </div>
  );
}

export default Composant1;

Question 2: Initialisation du state salaries 🙌
// App.js
import React, { useState, useEffect } from 'react';
import axios from 'axios';

function App() {
  const [salaries, setSalaries] = useState([]);

  useEffect(() => {
    const fetchSalaries = async () => {
      try {
        const response = await axios.get('http://localhost:8000/salaries');
        setSalaries(response.data);
      } catch (error) {
        console.error('Erreur lors de la récupération des salariés:', error);
      }
    };
*
    fetchSalaries();
  }, []);

  return (
    <div className="App">
      {/* Autres composants */}
    </div>
  );
}

export default App;

Question 4: Composant de recherche par service 💖

// composant3.js
import React, { useState } from 'react';

function Composant3({ salaries }) {
  const [serviceRecherche, setServiceRecherche] = useState('');
  const [resultats, setResultats] = useState([]);

  const handleRecherche = () => {
    const filtered = salaries.filter(salarie => 
      salarie.service?.nonser.toLowerCase().includes(serviceRecherche.toLowerCase())
    );
    setResultats(filtered);
  };

  return (
    <div>
      <h2>Recherche par service</h2>
      <div>
        <input
          type="text"
          value={serviceRecherche}
          onChange={(e) => setServiceRecherche(e.target.value)}
          placeholder="Entrez le nom du service"
        />
        <button onClick={handleRecherche}>Rechercher</button>
      </div>
*
      {resultats.length > 0 ? (
        <ul>
          {resultats.map(salarie => (
            <li key={salarie._id}>
              {salarie.nomsal} {salarie.prenomsal} - {salarie.fonction}
            </li>
          ))}
        </ul>
      ) : (
        <p>Aucun salarié n'est affecté à ce service</p>
      )}
    </div>
  );
}

export default Composant3;

