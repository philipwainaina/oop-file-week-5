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

class Smartphone:
    """
    A generic smartphone blueprint.
    """
    _IMEI_counter = 10_000_000_000_000  # static, auto-assigned unique IMEI

    def __init__(self, brand: str, model: str, storage_gb: int, color: str):
        self._brand = brand
        self._model = model
        self._storage_gb = storage_gb
        self._color = color
        self._IMEI = Smartphone._IMEI_counter
        Smartphone._IMEI_counter += 1
        self._battery_level = 100
        self._locked = True

    # ---------- Encapsulated helpers ----------
    @property
    def IMEI(self):
        return self._IMEI

    def unlock(self, pin: int):
        self._locked = False
        print(f"📱 {self._brand} {self._model} unlocked.")

    def charge(self, minutes: int):
        gained = min(minutes, 100 - self._battery_level)
        self._battery_level += gained
        print(f"🔋 Charged {gained}% — now at {self._battery_level}%")

    # ---------- Regular methods ----------
    def take_photo(self):
        if self._locked:
            print("❌ Unlock the phone first!")
        else:
            print(f"📸 Snap! Photo taken with {self._model}'s 48 MP camera.")

    def __str__(self):
        return (f"{self._color} {self._brand} {self._model} "
                f"({self._storage_gb} GB, IMEI: {self._IMEI})")


class GamingPhone(Smartphone):
    """
    Inherits from Smartphone and adds gaming-specific features.
    Demonstrates polymorphism by overriding `take_photo` and
    encapsulation via the hidden `_cooling_active` attribute.
    """
    def __init__(self, brand, model, storage_gb, color, cooling_system: str):
        super().__init__(brand, model, storage_gb, color)
        self._cooling_system = cooling_system
        self._cooling_active = False

    def enable_cooling(self):
        self._cooling_active = True
        print("🌀 Vapor-chamber cooling activated!")

    def take_photo(self):
        # Polymorphic override: gaming phones prioritize speed over quality
        if self._locked:
            print("❌ Unlock the phone first!")
        else:
            print("📸 Quick snap! Gaming mode photo (lower latency).")

    def boost_performance(self):
        print("🚀 Performance boosted for 10 minutes!")

        
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

class Vehicle:
    """Abstract base class for all vehicles."""
    def move(self):
        raise NotImplementedError("Subclasses must implement move()")


class Car(Vehicle):
    def move(self):
        print("🚗 Driving on the road!")


class Plane(Vehicle):
    def move(self):
        print("✈️ Flying through the sky!")


class Boat(Vehicle):
    def move(self):
        print("🚤 Sailing on water!")


# ---------------------------
# DEMO / TEST RUN
# ---------------------------

if __name__ == "__main__":
    # Activity 1 demo
    phone1 = Smartphone("Apple", "iPhone 15", 256, "Titanium")
    phone2 = GamingPhone("ASUS", "ROG Phone 8", 512, "Phantom Black", "Vapor-Chamber")

    print("=== Activity 1: Smartphone Classes ===")
    print(phone1)
    phone1.unlock(1234)
    phone1.take_photo()
    phone1.charge(30)

    print("\n" + str(phone2))
    phone2.unlock(9876)
    phone2.enable_cooling()
    phone2.take_photo()     # polymorphic override
    phone2.boost_performance()

    # Activity 2 demo
    print("\n=== Activity 2: Polymorphic Vehicles ===")
    vehicles = [Car(), Plane(), Boat()]
    for v in vehicles:
        v.move()
