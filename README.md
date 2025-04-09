# House Prices - Advanced Regression Techniques
კონკურსის მიზანი იყო, რომ მოცემული სახლის მონაცემების მიხედვით შეგვექმნა მოდელი,
რომელიც ახალ მონაცემებზე მოგვცემდა სავარაუდო გაყიდვის ფასს.
ჩემი მიდგომა იყო რომ ჯერ დამეთრეინებინა მოდელი 80%-ზე და დასტური მიმეღო 20%-ით kflod მეთოდით.

# რეპოზიტორიის სტრუქტურა
model_experiment.ipynb - აქ ვიმუშავე საწყის მონაცემებზე. გადავამუშავე/გადავაკეთე/გადავარჩიე და ასევე ვიპოვე საუკეთესო pipeline-ი
model_inference.ipynb - აქ შევქმენი საბმიშენი სატესტო მონაცემებით

# Feature Engineering
პირველი რაც ვქენი იყო ის, რომ ხარისხის არარიცხვობრივი ცვლადები დავმეფე წინასწარ მომზადებულ რიცხვებზე.
შემდგომ ყოველი არარიცხვობრივი სვეტი ავშიფრე OHE-ს მეშვეობით და ამოვიღე მაგიდიდან.
შემდეგ ყველა ნალ/ნან მნიშვნელობა ჩავანაცვლე mode-ით.

ამის მერე გავაერთიანე ისეთი სვეტები, რომლებიც ერთსა და იმავე პარამეტრზე საუბრობდა, მაგალითად:
შევქმენი ჯამური ფართობის ცვლადი რომელმაც აჯამა პირველი, მეორე სართულის ფართობები. ანალოგიური გავაკეთე სველ წერტილებზე/გარაჟზე/სხვენზე/საარდაფზე.

# Feature Selection
აქ პირდაპირ ავირჩიე ყველა სვეტი, რომელსაც გააჩნდა 0.5-ზე მეტი კორელაცია საბოლოო ფასთან (სადღაც 0.6-0.3-ში ვეძებე, overfit/underfit-ს შორის ვაკეთე ექსპერიმენტები)

# Training
გამოვცადე შემდეგი მოდელები:
 **Random Forest Regressor** 
 **Gradient Boosting Regressor**
 **XGBoost** 
 **RidgeCV** 
 **LassoCV** 
 **ElasticNetCV** 

გამოვიყენე `GridSearchCV` და `cross_val_score()` 5-fold validation-ით.
საბოლოო მოდელის შერჩევა მოხდა cross-validation საშუალო score-ების საფუძველზე (RMSE).

# MLflow Tracking

**MLflow ექსპერიმენტების ბმული**: https://dagshub.com/dshan21/ML_ASS_1.mlflow/#/experiments/0?searchFilter=&orderByKey=attributes.start_time&orderByAsc=false&startTime=ALL&lifecycleFilter=Active&modelVersionFilter=All+Runs&datasetsFilter=W10%3D
**ჩაწერილი მეტრიკები**:
 `RMSE`
 `R²`
**საუკეთესო მოდელის შედეგები**:
 `RMSE`: 29769.9795
 `Best RMSE`: 29150.5860
 `R²`: 0.8845

 საუკეთესო შედეგი:
![image](https://github.com/user-attachments/assets/73e6fd12-e7d1-44d4-9108-1fcb2fe1ef04)


