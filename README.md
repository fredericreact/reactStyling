# Inline style 
style attend un objet

```javascript
<label style={{color: !isValid ? 'red' : 'black'}}>Course Goal</label>       
```
Mais pas ouf inline style, better work with classes dynamically : 


```javascript
<div className={`form-control ${!isValid ? 'invalid' : ''}`}>
```

# Styled components and css module

Currently, le css scope n’est pas seulement limite a son componenet mais peut etre accessible dans tous les componennts

2 facons de regler ce problem : 

## 1. Styled components

```javascript
npm install --save styled-components
```

```javascript
const Button = styled.button`
 
 
  font: inherit;
  padding: 0.5rem 1.5rem;
  border: 1px solid #8b005d;
  color: white;
  background: #8b005d;
  box-shadow: 0 0 4px rgba(0, 0, 0, 0.26);
  cursor: pointer;
 
 
&:focus {
  outline: none;
}
 
&:hover,
&:active {
  background: #ac0e77;
  border-color: #ac0e77;
  box-shadow: 0 0 8px rgba(0, 0, 0, 0.26);
}
 
 
`;
```

Pour chaque class, ca va generer une classe unique

## 2. Css module


Importe de cette facon

```javascript
import styles from './Button.module.css';
```

Rename le css file

```javascript
Button.module.css
```

Applique la classe de cette facon

```javascript
className={styles.button}
```

Ca va creer des nom de classe unique mais plus clairs que styled components classes


Probleme avec cette syntaxe a cause du dash : invalid property name in js
```javascript
<div className={styles.form-control}>
```
On le regle comme ca :pour acceder a cette property
```javascript
<div className={styles['form-control']}>
```