# metrics Exercice 2 François TOUREILLE
## withdrawMoney method
### cyclomatic complexity value
5

### Refactoring proposé
Actuellement, toutes les conditions sont combinées dans un seul `if`, ce qui rend la complexité cyclomatique élevée.  
On peut remplacer ce `if` combiné par **4 vérifications séparées** avec des retours précoces (`return false`), supprimant ainsi le besoin d’un `else` et améliorant la lisibilité.  

De plus, pour isoler la logique de validation, on peut créer une méthode `canWithdraw(double amount)` qui contient toutes ces vérifications. La méthode `withdrawMoney()` devient alors simple : elle appelle `canWithdraw()` et effectue le retrait uniquement si la validation passe.  
