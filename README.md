# REACT-NOTES

## Setup and Installation of app Vite+React

```
1. go to https://tailwindcss.com/docs/guides/vite
2. create one project
 (npm create vite@latest my-project -- --template react)
 cd my-project
 npm i
 npm run dev
4. install tailwind css and config files
5. follow the instructions step
6. run and use.
npm run dev
```
## Todo Operation

### Create:
```
 const [tasks, setTasks] = useState([]);
    const addTask = title => {
        const newTasks = [...tasks, { title, completed: false }];
        setTasks(newTasks);
    };
```
### Read

 
