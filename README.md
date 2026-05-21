# Realtor AI Assistant

Realtor AI Assistant is a full-stack LangGraph real estate agent with a Python
backend and a React chat widget. It coordinates lead intake, property-search
criteria, database lookup, Google Calendar scheduling, and chat, SMS, and voice
entry points, with human approval before sensitive appointment actions.


## Backend: LangGraph Real Estate Agent

### Key Features

1. **Property Information Inquiry**  
   - Provides detailed property information, including square footage, pricing, condition, and amenities.

2. **Appointment Scheduling**  
   - Integrates with Google Calendar to facilitate the scheduling of property viewings and consultations.

3. **Multi-Platform Access**  
   - Accessible through chat-widgets, text messaging, and phone calls, ensuring real-time communication with clients across various channels.

4. **24/7 Availability**  
   - Operates around the clock, ensuring no inquiries go unanswered, reducing missed opportunities, and enhancing client satisfaction.

### Application Workflow

![AI agents graph](backend/graph.png)

1. **Initialization**: Starts at the `__start__` node.
2. **Main Interaction Hub**: The `main_agent` directs users to specific functionalities.
3. **Property Inquiry Process**: Routes users to `search_criteria_agent` and `query_database`.
4. **Appointment Management**: Guides users through the `appointment_agent` and `appointment_tools`.
5. **Human-in-the-Loop**: Ensures accuracy for complex tasks.
6. **Conclusion of Interaction**: Returns to `main_agent` and ends at `__end__` node.

### Backend Setup

1. **Install dependencies**  
   ```bash
   pip install -r requirements.txt
   ```

2. **Set up environment variables**  
   - Create a `.env` file in the root directory of the project.
   - Add the necessary environment variables.

3. **Download and set up data**  
   - Download the real estate dataset from [Kaggle](https://www.kaggle.com/datasets/ahmedshahriarsakib/usa-real-estate-dataset) and place it in the `/data` folder.
   - Run `csv_to_sql.py` to convert the CSV file into an SQL database.

4. **Run the main application**  
   - Terminal: `python main.py`
   - Local server: 
     1. Run the `ngrok.exe` file.
     2. Start the server: `uvicorn app-retell.server:app --reload`

## Frontend: Realtor AI Chat Widget

### Features

- Real-time chat interface with an AI assistant
- Responsive design for various screen sizes
- WebSocket integration for live communication
- Tailwind CSS for styling
- TypeScript for type safety

### Frontend Setup

1. **Install dependencies**:
   ```bash
   npm install
   ```
   or
   ```bash
   yarn install
   ```

2. Create a `.env` file in the root directory and add any necessary environment variables.

### Development

To run the development server:

```
npm run dev
```
or
```
yarn dev
```

Open [http://localhost:5173](http://localhost:5173) to view it in the browser.

### Building for Production

To create a production build:

```
npm run build
```
or
```
yarn build
```

### Usage

To use the ChatbotWidget in your React application:

```jsx
import ChatbotWidget from './components/chatbot-widget'

function App() {
  return (
    <div className="App">
      <ChatbotWidget websiteId="your-website-id" />
    </div>
  )
}
```

Replace `"your-website-id"` with the appropriate identifier for your website.

### Configuration

- The WebSocket connection URL is currently set to `ws://127.0.0.1:8000/ws/${websiteId}/${threadId}`. Update this in `chatbot-widget.tsx` if your backend is hosted elsewhere.
- Tailwind CSS configuration can be modified in `tailwind.config.js`.
- TypeScript configuration is split between `tsconfig.json`, `tsconfig.app.json`, and `tsconfig.node.json`.

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request for either the backend or frontend components.

## License

This project is licensed under the GNU General Public License v3.0. See the LICENSE file in the backend directory for details.
