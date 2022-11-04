# Create a new Boilerplate

Open terminal and create a new entity using symfony CLI:
```bash
#Complete the wizard
php bin/console make:entity

#Create migration file
php bin/console make:migration

#execute migration so the table is created in DB
php bin/console doctrine:migrations:migrate

#Create a new CRUD
php bin/console make:crud
```

Now we have to specify some changes in the generated code based on our boilerplate
```php
//open src/Controller/BoilerplateController.php
//this file contains the CRUD controller for the Boilerplate entity.
//we will copy paste some things from here to our new controller

//open the new controller src/Controller/*Entity*Controller.php
//on top of the file copy the IsGranted annotation and add any additional route name
/**
 * @Route("/admin/entity")
 * @IsGranted("ROLE_ADMIN")
 */
class EntityController...

//extend to the AptoAbstractController class instead of the AbstractController
class EntityController extends AptoAbstractController

//copy the index method from the BoilerplateController to the new controller
//change the BoilerplateRepository $boilerplateRepository to the new entity repository
//change the $boilerplateRepository->count([]) to $entityRepository->count([])
//change the $boilerplateRepository->findBy([]) to $entityRepository->findBy([])
//change the boilerplate/index.html.twig to entity/index.html.twig
//this will allow us to filter the results based on the request query parameters
//and also to add pagination
public function index(Request $request,EntityRepository $entityRepository): Response
{

    $currentPage = $request->get('_page', 1);
    $offset = ($currentPage - 1) * self::PER_PAGE;

    $total = $entityRepository->count([]);
    $entities = $entityRepository->findBy([],[],self::PER_PAGE,$offset);

    return $this->render('entity/index.html.twig', [
        'entities' => [
            'items'=>$entities,
            'total' => $total,
            'perPage' => self::PER_PAGE,
            'offset' => $offset,
        ],
    ]);
}

//on the new function, add the $this->cache->flushdb(); when the entity is saved
//this will clear the Redis cache for the entity
if ($form->isSubmitted() && $form->isValid()) {
    $boilerplateRepository->add($boilerplate, true);

    //add this line
    $this->cache->flushdb();

    return $this->redirectToRoute('app_boilerplate_index', [], Response::HTTP_SEE_OTHER);
}
```

Now we have to tell doctrine to cache the entity
```php
//open src/Entity/Entity.php that was created by the crud generator
//add the following annotation to the class

/**
 ...
 * @Cache(usage="NONSTRICT_READ_WRITE", region="region")
 */
```

Add a save button to the Entity form
```php
//open src/Form/EntityType.php
//add the following line to the button of the form builder
$builder
    ...
    ->add('save', SubmitType::class, [
        'label' => 'Save',
    ])
```

Now we will copy paste all the boilerplate twig files to the new entity
```bash
#copy the boilerplate folder to the new entity folder
cp -r templates/boilerplate templates/entity
```

Add the menu item to a menu
```php
//open src/Service/MenuService.php
//on the appropriate menu add the following line
//that contains the route name
//now open the menu template by ctrl+clicking on the menu name
const BACK_MENU_BOTTOM = [
        ...
        'entity/_menu.item.html.twig',
        ...
    ];
```

Add a menu image to the assets folder
```bash
#open the assets/images folder
#add a new svg with the name of the entity
entity.svg
```

Now we will change the index template to show the new entity
```html
#open templates/entity/index.html.twig
#change the th to match our new entity
<th scope="col" class="whitespace-nowrap text-sm font-medium text-gray-900 px-6 py-4 text-left">
    name
</th>
<th scope="col" class="whitespace-nowrap text-sm font-medium text-gray-900 px-6 py-4 text-left">
    content
</th>
<th scope="col" class="whitespace-nowrap text-sm font-medium text-gray-900 px-6 py-4 text-left">
    User
</th>

#also change th td to match the new entity
<td class="text-sm text-gray-900 font-light px-6 py-4 whitespace-nowrap">
    {{ entity_item.name }}
</td>
<td class="text-sm text-gray-900 font-light px-6 py-4 whitespace-nowrap">
    {{ entity_item.content }}
</td>
<td class="text-sm text-gray-900 font-light px-6 py-4 whitespace-nowrap">
    {{ entity_item.user.userIdentifier }}
</td>
```