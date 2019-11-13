#################
Java 8
#################

Java 8 new features
=======================

Take it away, Eric the Orchestra Leader!

    | A one, two, a one two three four
    |
    | Half a bee, philosophically,
    |     must, *ipso facto*, half not be.
    | But half the bee has got to be,
    |     *vis a vis* its entity.  D'you see?
    |
    | But can a bee be said to be
    |     or not to be an entire bee,
    |         when half the bee is not a bee,
    |             due to some ancient injury?
    |
    | Singing...

Static Method
****************

.. code-block:: java
   :linenos:

    public interface Vehicle {
        static String producer() {
            return "N&F Vehicles";
        }
    }

invoke::

    String producer = Vehicle.producer();


Default Method
****************

.. code-block:: java
   :linenos:

    default String getOverview() {
        return "ATV made by " + producer();
    }

invoke::

    Vehicle vehicle = new VehicleImpl();
    String overview = vehicle.getOverview();


Optional
****************
.. code-block:: java
   :linenos:

    // demo 1
    List<String> list = getList();
    List<String> listOpt = list != null ? list : new ArrayList<>();

    List<String> listOpt = getList().orElseGet(() -> new ArrayList<>());

    // demo 2
    User user = getUser();
    if (user != null) {
        Address address = user.getAddress();
        if (address != null) {
            String street = address.getStreet();
            if (street != null) {
                return street;
            }
        }
    }
    return "not specified";

    Optional<User> user = Optional.ofNullable(getUser());
    String result = user
    .map(User::getAddress)
    .map(Address::getStreet)
    .orElse("not specified");


    Optional<OptionalUser> optionalUser = Optional.ofNullable(getOptionalUser());
    String result = optionalUser
    .flatMap(OptionalUser::getAddress)
    .flatMap(OptionalAddress::getStreet)
    .orElse("not specified");



参考
=======
https://www.baeldung.com/java-8-new-features