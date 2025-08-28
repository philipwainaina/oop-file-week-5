📱 Activity 1 – Smartphone Design
Base Class: Smartphone
Attributes (initialized via constructor)
brand, model, storage_gb, color
Auto-generated _IMEI (unique per object)
Private _battery_level & _locked flag (encapsulation)
Methods
unlock(pin) – unlocks the phone
charge(minutes) – increases battery level
take_photo() – prints a camera message
__str__() – human-readable description
Derived Class: GamingPhone (Inheritance)
Extends Smartphone with:
_cooling_system (e.g., "Vapor-Chamber")
enable_cooling() – turns cooling on
boost_performance() – temporary speed boost
Polymorphic override of take_photo() – faster but lower-quality shots
🚗 Activity 2 – Polymorphism Challenge
Abstract Base: Vehicle
Defines interface move() (not implemented).
Concrete Subclasses
Car → prints 🚗 Driving on the road!
Plane → prints ✈️ Flying through the sky!
Boat → prints 🚤 Sailing on water!
Looping over a list of Vehicle objects demonstrates dynamic polymorphism—each subclass provides its own version of move().
🧪 Experiment Ideas
Add new phone types (FoldablePhone, CameraPhone) with unique overrides.
Introduce more vehicles (Bike, Submarine) or a start_engine() method.
Persist objects with pickle or json.
Build a simple CLI menu instead of the hard-coded demo.
