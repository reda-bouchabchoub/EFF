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
