# Tree Problem
```PHP
// 0
// ├── 100
// │   ├── 150
// │   │   └── 200
// │   └── 250
// └── 500

$allProductsCategories = [
	'id' => 0,
	'children' => [
		[
			'id' => 100,
			'children' => [
				[
					'id' => 150,
					'children' => [
						[
							'id' => 200,
							'children' => [],
						],
					],
				],
				[
					'id' => 250,
					'children' => [],
				],
			],
		],
		[
			'id' => 500,
			'children' => [],
		],
	],

];

$productCategories = [
	500,
	100,
	200,
	600,
];
```

Έχουμε δύο μεταβλητές `$allProductsCategories` και `$productCategories`.  
Η `$allProductsCategories` αναπαριστά τη διάρθρωση των κατηγοριών των προϊόντων ενός καταστήματος (`tree` structure) και η `$productCategories` τις κατηγορίες στις οποίες ανήκει ένα προϊόν. 

---
### Ζητούμενα

---
- Πρέπει να δημιουργηθεί ένας πίνακας `$allAncestors`, ο οποίος έχει τόσες θέσεις όσα είναι και τα `leaves` (φύλλα) της `$allProductsCategories` που υπάρχουν στην `$productCategories`.
- Κάθε θέση του παραπάνω πίνακα είναι ένας άλλος πίνακας που περιέχει τα `nodes` του `path` σε κάθε κλειδί του. Η αναφορά στο `root` πρέπει να παραλείπεται:
πχ `[100, 150, 200]` και όχι `[0, 100, 150, 200]`

---
### Προϋποθέσεις

---
- Η προσπέλαση του δέντρου πρέπει να γίνει με αναδρομική συνάρτηση.
- Επειδή η αναζήτηση σε δέντρο είναι κοστοβόρα, πρέπει να γίνουν μόνο οι πολύ απαραίτητες αναζητήσεις.
---
### Επεξηγήσεις και συμπληρωματικές πληροφορίες

---
- Κάθε διαδρομή είναι βέβαιο ότι τα `id` που την αποτελούν είναι πάντοτε μικρότερα των `id` των αμέσως επόμενων διαδρομών.
---

### Αποτέλεσμα

---
- Ο κώδικας είναι έγκυρος όταν κάνοντας print της `$allAncestors` έχει ως αποτέλεσμα τον παρακάτω πίνακα:
```
Array
(
    [0] => Array
        (
            [0] => 500
        )

    [1] => Array
        (
            [0] => 100
            [1] => 150
            [2] => 200
        )

)
```
- και η προσπέλαση του πίνακα `$allProductsCategories` αναφορικά με την αναδρομική αναζήτηση να γίνει **ΜΟΝΟ** 3 φορές. 

---
### Σημείωση

---
Αν θεωρείς ότι κάτι πρέπει να λυθεί με άλλον τρόπο, να το κάνεις και να δικαιολογήσεις την προσέγγισή σου
