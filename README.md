# evote-movie-2019-09-movie-objects

Part of the progressive Movie Voting website project at:
https://github.com/dr-matt-smith/evote-movie-2019

The project has been refactored as follows:

- in directory `/src` a new class `Movie.php` is created:

    ```php
      namespace Mattsmithdev;
            
      class Movie
      {
          private $id;
          private $title;
          private $price;
      
          /**
           * @return mixed
           */
          public function getId()
          {
              return $this->id;
          }
        
          ... getters/setters for all properties
    ```

- the constructor method of class `/src/MovieRepository.php` is refacted to create 3 `Movie` objects and store them in private array property `$this->movies`:

    ```php
          public function __construct()
          {
              $movie1 = new Movie();
              $movie1->setId(1);
              $movie1->setTitle('Jaws');
              $movie1->setPrice(9.99);
      
              $movie2 = new Movie();
              $movie2->setId(2);
              $movie2->setTitle('Aliens');
              $movie2->setPrice(19.99);
      
      
              $movie3 = new Movie();
              $movie3->setId(3);
              $movie3->setTitle('Shrek');
              $movie3->setPrice(10.00);
      
      
              $this->movies[] = $movie1;
              $this->movies[] = $movie2;
              $this->movies[] = $movie3;
          }
    ```

- the template to loop through all movies in `/templates/list.php` is refactored to use the public `get` methods to retrieve the id/title/price values from each `Movie` object in the array:

    ```php
          <?php
              foreach($movies as $movie):
          ?>      
              <tr>
                  <td><?= $movie->getId() ?></td>
                  <td><?= $movie->getTitle() ?></td>
                  <td>&euro; <?= $movie->getPrice() ?></td>
              </tr>
          <?php
              endforeach;
          ?>
    ```

