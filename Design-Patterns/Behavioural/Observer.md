# Observer 

## Problem that it is trying to solve

Components state may be dependant when another component changes states, instead of this component sending an update to every other component with this design pattern we can have more flexability with which ocmpnenets can 'observe' others and update them accordinly. 

## What does it aim to acheive 

Creates a subscription model that notifies components when a state of one model changes 

The subscribers/listenrs get are mamanged by the eventmanager and they are notified once the the event they are subbscribed too is updated 

```cpp
class IEventListener{
    public:
    virtual void update(filename)=0;
}

class EmailAlertListener : IEventListener{
    public:
    void update(filename) override{
        //some implementation logic 
    }
}

class LoggingListener : IEventListener{
    public:
    void update(filename) override{
        //some implementation logic 
    }
}

class EventManger{
    private: 
    unordered_map<string, vector<IEventListener>> subscriberModel;
    public:
    void subscribe(string typeOfEvent, IEventListener eventListener){
    subscriberModel[typeOfEvent].push_back(eventListener);
    };
    void unsubscribe(string typeOfEvent, IEventListener eventListener){
        //erase(remvove from the vector)
        erase(remove(subscriberModel[typeOfEvent].begin(), subscriberModel[typeOfEvent].end(), eventListner), subscriberModel[typeOfEvent].end()); 
    };
    void notify(string event, stiring filename){
        for(auto* listener : subscriberModel[event]){
            listener->update(filename);
        }
    };
}

class Editor{
    private:
    EventManager events;

    public:
    Editor();
    void openfile();
    void closefile();
    EventManager getEvents(){return events;}
}

int main(){
    LoggingListener logger;
    EmailAlertListener emailAlerts;

    // Subscribe observers to specific events
    editor.getEvents().subscribe("open", &logger);
    editor.getEvents().subscribe("save", &emailAlerts);

    // Trigger events
    editor.openFile("document.txt");

    return 0;
}


// #include <iostream>
// #include <string>
// #include <vector>
// #include <unordered_map>
// #include <memory>

// using namespace std;

// class IEventListener {
// public:
//     virtual void update(const string& filename) = 0;
//     virtual ~IEventListener() = default;
// };

// class LoggingListener : public IEventListener {
// public:
//     void update(const string& filename) override {
//         cout << "Logging: " << filename << " opened\n";
//     }
// };

// class EmailAlertListener : public IEventListener {
// public:
//     void update(const string& filename) override {
//         cout << "Email sent: " << filename << '\n';
//     }
// };

// class EventManager {
// private:
//     unordered_map<string, vector<IEventListener*>> listeners;

// public:
//     void subscribe(const string& event, IEventListener* listener) {
//         listeners[event].push_back(listener);
//     }

//     void notify(const string& event, const string& filename) {
//         for (auto* listener : listeners[event]) {
//             listener->update(filename);
//         }
//     }
// };

// class Editor {
// private:
//     EventManager events;

// public:
//     EventManager& getEvents() {
//         return events;
//     }

//     void openFile(const string& filename) {
//         cout << "Opening " << filename << '\n';

//         events.notify("open", filename);
//     }
// };
```