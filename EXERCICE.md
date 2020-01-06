Bienvenue !

Maintenant que la structure de votre code est complète, vous avez des `actions`, des `reducers`, et un `store` fonctionnel qui vous permettant de mettre à jour votre `state` global et le rester. Suivez cet exercice afin de pouvoir les utiliser dans votre application React.

De la même manière que pour `VisibleTodoList`, nous allons créer le container `FilterLink` dont le rôle est de gérer les filtres : il s'agit des boutons qui affichent toutes les todos, uniquement celles qui sont terminées ou uniquement celles qui sont en cours.

1. Avez-vous importez tous ce qui est nécessaire pour le bon fonctionnement de notre `containers` ?

Dans le fichier `/src/containers/FilterLink/index.js`, importez le nécessaire pour que votre future `containers` puisse fonctionner. Pour ce faire, vous aurez besoin :
- De la fonction `connect` présente dans la librairie `react-redux`
- De l'action `setVisibilityFilter` présente dans notre fichier action (`../../actions/index.js`)
- Du `component` nommé `Link` qui sera la base de ce `containers` (`../../components/Link`)

**Important :** N'oubliez pas que les composants sont exportés par défaut, nous devons donc les importer comme ceci : `import MyComponent from '../components/MyComponent'`

2. Avez-vous créé la fonction `mapStateToProps` ?

Maintenant, définissez la constante `mapStateToProps` qui sera une fonction qui prendra pour arguments `state` et `ownState`. Cette fonction retournera un objet dont la seule clé sera `active`. Cette clé aura pour valeur `true` si `ownProps.filter` est strictement égal à `state.visibilityFilter`.

**Exemple :**
```javascript
const mapStateToProps = (state, ownProps) => ({
	active: ownProps.userFilter === state.visibilityUserFilter
})
```

3. Avez-vous créé la fonction `mapDispatchToProps` ?

Définissez maintenant une constante nommé `mapDispatchToProps` qui sera une fonction qui prendra pour arguments `dispatch` et `ownProps`.  Cette fonction retournera un objet avec pour unique clé `setFilter`. Elle prendra pour valeur une fonction sans argument *(utilisez une `arrow function`)* qui retournera un `dispatch(setVisibilityFilter(ownProps.filter))`. Il s'agit de la manière la plus simple pour `dispatch` une action unique, donc pas besoin d'utiliser `bindActionCreators()`.

**Exemple :**
```javascript
const mapDispatchToProps = (dispatch, ownProps) => ({
	setUserFilter: () => {
		dispatch(setVisibilityUserFilter(ownProps.filter))
	}
})
```

4. Avez-vous correctement construit la méthode `connect` en incluant `mapStateToProps`, `mapDispatchToProps` et en incluant le composant `Link` ?

Pour terminer, utilisez la fonction `connect` pour lier vos fonctions `mapStateToProps` et `mapDispatchToProps` au composant `Link`. N'oubliez pas d'exporter `connect` par défaut.

**Exemple :**
```javascript
export default connect(
	mapStateToProps,
	mapDispatchToProps
)(UserLink)
```