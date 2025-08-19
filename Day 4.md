# 📅 Day 4: Controlled Forms & API Integration
## 🎯 Theory
1. Controlled Forms

In React, form inputs are tied to component state.

The input value is always driven by state, making it predictable and easy to manipulate.

function ControlledForm() {
  const [name, setName] = React.useState("");
  
  return (
    <div>
      <input 
        type="text" 
        value={name} 
        onChange={(e) => setName(e.target.value)} 
      />
      <p>Live Preview: {name}</p>
    </div>
  );
}


✅ Advantage: Ensures data consistency between UI and logic.

2. API Calls in React

Done using fetch() or libraries like axios.

Typically inside useEffect() or triggered by events.

function FetchUsers() {
  const [users, setUsers] = React.useState([]);

  React.useEffect(() => {
    fetch("https://api.github.com/users")
      .then(res => res.json())
      .then(data => setUsers(data));
  }, []);

  return (
    <ul>
      {users.map(user => <li key={user.id}>{user.login}</li>)}
    </ul>
  );
}

## 🌍 Industry Use Case

Job portals use controlled forms (search filters) + API calls (fetch job listings).

## 💡 Creative Use Case

Auto-generate a study planner: Take subjects + durations as inputs, call AI endpoint (mock for now) → return structured plan.

## 📝 Assignments

Form with Live Preview

Create a form with name & age fields.

Show live preview below the form.

function PreviewForm() {
  const [name, setName] = React.useState("");
  const [age, setAge] = React.useState("");

  return (
    <div>
      <input 
        placeholder="Enter name"
        value={name}
        onChange={(e) => setName(e.target.value)}
      />
      <input 
        type="number"
        placeholder="Enter age"
        value={age}
        onChange={(e) => setAge(e.target.value)}
      />
      <p>👤 {name} | 🎂 {age}</p>
    </div>
  );
}


Fetch GitHub Users

Fetch and display GitHub usernames.

function GitHubUsers() {
  const [users, setUsers] = React.useState([]);

  React.useEffect(() => {
    fetch("https://api.github.com/users")
      .then(res => res.json())
      .then(data => setUsers(data));
  }, []);

  return (
    <div>
      <h3>GitHub Users</h3>
      <ul>
        {users.map(user => <li key={user.id}>{user.login}</li>)}
      </ul>
    </div>
  );
}

## 🚀 Project Task
Add Study Planner Section

Input: subject + duration.

On submit, generate a mock AI study plan (using hardcoded or JSONPlaceholder).

function StudyPlanner() {
  const [subject, setSubject] = React.useState("");
  const [duration, setDuration] = React.useState("");
  const [plan, setPlan] = React.useState("");

  const generatePlan = async () => {
    // Mock AI response
    setPlan(`📚 Study ${subject} for ${duration} hours. Take short breaks!`);
  };

  return (
    <div>
      <h3>Study Planner</h3>
      <input 
        placeholder="Subject"
        value={subject}
        onChange={(e) => setSubject(e.target.value)}
      />
      <input 
        type="number"
        placeholder="Duration (hrs)"
        value={duration}
        onChange={(e) => setDuration(e.target.value)}
      />
      <button onClick={generatePlan}>Generate Plan</button>
      {plan && <p>{plan}</p>}
    </div>
  );
}
