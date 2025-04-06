import React, { useState } from 'react';

function App() {
  const [items, setItems] = useState([]);
  const [inputValue, setInputValue] = useState('');

  const handleAddItem = (e) => {
    e.preventDefault();
    if (inputValue.trim() !== '') {
      setItems([...items, inputValue]);
      setInputValue('');
    }
  };

  return (
    <div style={styles.appContainer}>
      <h1 style={styles.header}>Dynamic Item List</h1>
      
      <form onSubmit={handleAddItem} style={styles.inputForm}>
        <input
          type="text"
          value={inputValue}
          onChange={(e) => setInputValue(e.target.value)}
          placeholder="Enter item..."
          style={styles.itemInput}
        />
        <button type="submit" style={styles.addButton}>
          Add Item
        </button>
      </form>

      <div style={styles.listContainer}>
        {items.length === 0 ? (
          <p style={styles.emptyMessage}>Your list is empty. Add some items!</p>
        ) : (
          <ul style={styles.itemList}>
            {items.map((item, index) => (
              <li key={index} style={styles.listItem}>
                {item}
              </li>
            ))}
          </ul>
        )}
      </div>
    </div>
  );
}

const styles = {
  appContainer: {
    maxWidth: '500px',
    margin: '2rem auto',
    padding: '1.5rem',
    fontFamily: "'Segoe UI', Tahoma, Geneva, Verdana, sans-serif",
    background: '#f8f9fa',
    borderRadius: '8px',
    boxShadow: '0 2px 10px rgba(0, 0, 0, 0.1)'
  },
  header: {
    textAlign: 'center',
    color: '#2c3e50',
    marginBottom: '1.5rem'
  },
  inputForm: {
    display: 'flex',
    gap: '0.5rem',
    marginBottom: '1.5rem'
  },
  itemInput: {
    flex: 1,
    padding: '0.75rem',
    border: '1px solid #ced4da',
    borderRadius: '4px',
    fontSize: '1rem',
    transition: 'border-color 0.3s'
  },
  addButton: {
    padding: '0.75rem 1.5rem',
    backgroundColor: '#4dabf7',
    color: 'white',
    border: 'none',
    borderRadius: '4px',
    cursor: 'pointer',
    fontSize: '1rem',
    transition: 'background-color 0.3s'
  },
  listContainer: {
    background: 'white',
    borderRadius: '6px',
    padding: '1rem',
    boxShadow: '0 1px 3px rgba(0, 0, 0, 0.1)',
    minHeight: '200px'
  },
  emptyMessage: {
    textAlign: 'center',
    color: '#868e96',
    fontStyle: 'italic',
    padding: '2rem 0'
  },
  itemList: {
    listStyle: 'none',
    padding: 0,
    margin: 0
  },
  listItem: {
    padding: '0.75rem 1rem',
    marginBottom: '0.5rem',
    background: 'white',
    border: '1px solid #e9ecef',
    borderRadius: '4px',
    transition: 'all 0.2s',
    display: 'flex',
    alignItems: 'center'
  }
};

// Add hover effects using JavaScript
styles.itemInput[':focus'] = {
  outline: 'none',
  borderColor: '#4dabf7',
  boxShadow: '0 0 0 2px rgba(77, 171, 247, 0.2)'
};

styles.addButton[':hover'] = {
  backgroundColor: '#339af0'
};

styles.addButton[':active'] = {
  backgroundColor: '#228be6'
};

styles.listItem[':hover'] = {
  background: '#f8f9fa',
  transform: 'translateX(3px)'
};

export default App;
