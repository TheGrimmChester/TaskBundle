![AWHS Logo](https://nicolasmeloni.ovh/images/awhspanel.png)

# TaskBundle
TaskBundle of AWHSPanel
This package provides a basic system for managing tasks in the background.

## Requirements
* Have installed the [foundation](https://github.com/TheGrimmChester/AWHSPanel/blob/master/README.md)  
* Have installed the [UserBundle](https://github.com/TheGrimmChester/UserBundle/blob/master/README.md)

## Installation
1. Clone this bundle inside `src/AWHS/` directory.
2. Enable the bundle in the kernel by adding the following line right after `//AWHS Bundles` in `app/AppKernel.php` file:  
`new AWHS\TaskBundle\AWHSTaskBundle(),`
3. Load data fixtures: `php bin/console doctrine:fixtures:load --fixtures=src/AWHS/TaskBundle/DataFixtures/ORM --append`
4. Add the following code to the `src/AWHS/UserBundle/Entity/User.php` file:
```yaml
/**
 * @ORM\OneToMany(targetEntity="AWHS\TaskBundle\Entity\Task", mappedBy="user")
 * @ORM\OrderBy({"id" = "DESC"})
 */
private $tasks;

/**
 * Get tasks
 *
 * @return \Doctrine\Common\Collections\Collection
 */
public function getTasks()
{
    return $this->tasks;
}
```

## TODO
- [ ] Multilingual
- [ ] Refactoring old code.
