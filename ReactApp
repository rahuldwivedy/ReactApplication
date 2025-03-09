import { BrowserRouter as Router, Route, Routes, Link, useNavigate } from 'react-router-dom';
import { useState } from 'react';
import { motion } from 'framer-motion';

const Home = () => {
  const navigate = useNavigate();
  return (
    <motion.div 
      className="min-h-screen flex flex-col items-center justify-center text-center p-6"
      initial={{ opacity: 0, y: -50 }} 
      animate={{ opacity: 1, y: 0 }} 
      transition={{ duration: 0.8 }}
    >
      <h1 className="text-4xl font-bold">Connecting People Across Faiths & Interests</h1>
      <p className="mt-4 text-lg">Connecting people of all faiths through events and community support.</p>
      <motion.button 
        onClick={() => navigate('/events')} 
        className="mt-6 bg-blue-600 text-white px-6 py-2 rounded-lg"
        whileHover={{ scale: 1.1 }}
      >
        Explore Events
      </motion.button>
    </motion.div>
  );
};

const EventListing = () => {
  const [events, setEvents] = useState([
    { title: "Charity Drive", date: "2025-04-12", location: "City Center", category: "Charity" },
    { title: "Interfaith Meetup", date: "2025-05-22", location: "Community Hall", category: "Social" }
  ]);
  const [categoryFilter, setCategoryFilter] = useState("");
  const [newEvent, setNewEvent] = useState({ title: "", date: "", location: "", category: "" });

  const filteredEvents = categoryFilter ? events.filter(event => event.category === categoryFilter) : events;

  const addEvent = () => {
    if (newEvent.title && newEvent.date && newEvent.location && newEvent.category) {
      setEvents([...events, newEvent]);
      setNewEvent({ title: "", date: "", location: "", category: "" });
    }
  };

  return (
    <motion.div className="p-6"
      initial={{ opacity: 0 }} 
      animate={{ opacity: 1 }} 
      transition={{ duration: 0.8 }}
    >
      <h2 className="text-2xl font-bold">Event Listings</h2>
      <select onChange={e => setCategoryFilter(e.target.value)} className="border p-2 mt-4">
        <option value="">All Categories</option>
        <option value="Religious">Religious</option>
        <option value="Social">Social</option>
        <option value="Charity">Charity</option>
      </select>
      <ul className="mt-4">
        {filteredEvents.map((event, index) => (
          <motion.li key={index} className="border p-4 mb-2"
            initial={{ opacity: 0, x: -20 }} 
            animate={{ opacity: 1, x: 0 }} 
            transition={{ duration: 0.5, delay: index * 0.1 }}
          >
            <h3 className="font-bold">{event.title}</h3>
            <p>{event.date} - {event.location}</p>
            <p>Category: {event.category}</p>
          </motion.li>
        ))}
      </ul>
      <h3 className="text-xl mt-6">Add New Event</h3>
      <input type="text" placeholder="Title" value={newEvent.title} onChange={e => setNewEvent({ ...newEvent, title: e.target.value })} className="border p-2 block mt-2" />
      <input type="date" value={newEvent.date} onChange={e => setNewEvent({ ...newEvent, date: e.target.value })} className="border p-2 block mt-2" />
      <input type="text" placeholder="Location" value={newEvent.location} onChange={e => setNewEvent({ ...newEvent, location: e.target.value })} className="border p-2 block mt-2" />
      <select value={newEvent.category} onChange={e => setNewEvent({ ...newEvent, category: e.target.value })} className="border p-2 block mt-2">
        <option value="">Select Category</option>
        <option value="Religious">Religious</option>
        <option value="Social">Social</option>
        <option value="Charity">Charity</option>
      </select>
      <motion.button onClick={addEvent} className="mt-4 bg-green-600 text-white px-4 py-2 rounded-lg"
        whileHover={{ scale: 1.1 }}
      >
        Add Event
      </motion.button>
    </motion.div>
  );
};

const App = () => {
  return (
    <Router>
      <nav className="p-4 bg-gray-800 text-white flex justify-between">
        <span className="font-bold">Communion App</span>
        <div>
          <Link to="/" className="mx-2">Home</Link>
          <Link to="/events" className="mx-2">Events</Link>
          <Link to="/about" className="mx-2">About</Link>
        </div>
      </nav>
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/events" element={<EventListing />} />
      </Routes>
    </Router>
  );
};

export default App;
