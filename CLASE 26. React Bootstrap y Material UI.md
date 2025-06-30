# 26. React Bootstrap & Material UI.

En esta clase aprenderemos a utilizar ***frameworks*** ya optimizados reescritos especialmente para ***React***.

Los cuales son:

	- React Bootstrap.

	https://react-bootstrap.github.io/

	- Material UI. 

	https://mui.com/material-ui/

---
## React Bootstrap

Veamos como podemos utilizar ***React Bootstrap*** en un proyecto de utilizarlo:
### 1. Instalación de framework en proyecto.

Para utilizar el ***framework*** de ***React Bootstrap*** es necesario instalarlo en nuestro proyecto:

~~~
npm install react-bootstrap bootstrap
~~~

***Nota:*** Se recomienda visualizar la ***documentación oficial*** por si existe algun cambio.

***Nota:*** Podemos visualizar la ***instalación*** dentro de nuestro archivo `package.json`.

Con valores similares a:

~~~json
	"bootstrap": "^5.3.3",
	"react-bootstrap": "^2.10.7",
~~~
### 2. Importación de hoja de estilos CSS de react bootstrap.

Y agregar a nuestro componente el ***import*** para aplicar los ***estilos*** de ***bootstrap***:

~~~jsx
import 'bootstrap/dist/css/bootstrap.min.css';
~~~

### 3. Utilización de componentes React Bootstrap.

Dentro de la ***documentación*** podemos encontrar el apartado de ***componentes***, donde existen muchos ***elementos*** a utilizar, junto con su ***código JSX*** a copiar y pegar dentro de nuestro archivo `.jsx`.

Como un ejemplo de estos:

~~~jsx
import Container from 'react-bootstrap/Container';
import Nav from 'react-bootstrap/Nav';
import Navbar from 'react-bootstrap/Navbar';
import NavDropdown from 'react-bootstrap/NavDropdown';

function BasicExample() {
  return (
    <Navbar expand="lg" className="bg-body-tertiary">
      <Container>
        <Navbar.Brand href="#home">React-Bootstrap</Navbar.Brand>
        <Navbar.Toggle aria-controls="basic-navbar-nav" />
        <Navbar.Collapse id="basic-navbar-nav">
          <Nav className="me-auto">
            <Nav.Link href="#home">Home</Nav.Link>
            <Nav.Link href="#link">Link</Nav.Link>
            <NavDropdown title="Dropdown" id="basic-nav-dropdown">
              <NavDropdown.Item href="#action/3.1">Action</NavDropdown.Item>
              <NavDropdown.Item href="#action/3.2">
                Another action
              </NavDropdown.Item>
              <NavDropdown.Item href="#action/3.3">Something</NavDropdown.Item>
              <NavDropdown.Divider />
              <NavDropdown.Item href="#action/3.4">
                Separated link
              </NavDropdown.Item>
            </NavDropdown>
          </Nav>
        </Navbar.Collapse>
      </Container>
    </Navbar>
  );
}

export default BasicExample;
~~~

¡Listo!, tu componente ya esta listo para utilizar en nuestro proyecto.

***Nota:*** No olvides agregar el ***import*** de la ***hoja*** `.css`.

---
### Código de ejemplo completo.

Veamos el ***código completo*** del ejemplo:

En el archivo de componente llamado`ReactBootstrap.jsx`:

~~~jsx
import React from "react";
import 'bootstrap/dist/css/bootstrap.min.css';

import Container from 'react-bootstrap/Container';
import Nav from 'react-bootstrap/Nav';
import Navbar from 'react-bootstrap/Navbar';
import NavDropdown from 'react-bootstrap/NavDropdown';

export function BasicExample() {
	return (
		<Navbar expand="lg" className="bg-body-tertiary">
			<Container>
				<Navbar.Brand href="#home">React-Bootstrap</Navbar.Brand>
				<Navbar.Toggle aria-controls="basic-navbar-nav" />
				<Navbar.Collapse id="basic-navbar-nav">
					<Nav className="me-auto">
						<Nav.Link href="#home">Home</Nav.Link>
						<Nav.Link href="#link">Link</Nav.Link>
						<NavDropdown title="Dropdown" id="basic-nav-dropdown">
								<NavDropdown.Item href="#action/3.1">
									Action
								</NavDropdown.Item>
								<NavDropdown.Item href="#action/3.2">
									Another action
								</NavDropdown.Item>
								<NavDropdown.Item href="#action/3.3">
									Something
								</NavDropdown.Item>
							<NavDropdown.Divider />
							<NavDropdown.Item href="#action/3.4">
								Separated link
							</NavDropdown.Item>
						</NavDropdown>
					</Nav>
				</Navbar.Collapse>
			</Container>
		</Navbar>
	);
}

export default function ReactBootstrap () {
	return (
		<>
			<h2>React Bootstrap</h2>
		</>
	);
}
~~~

En el `App.js`:

~~~jsx
import ReactBootstrap, {BasicExample} from './components/ReactBootstrap.jsx';

function App() {
	return (
		<div>
			<h1>Frameworks CSS con React</h1>
			<ReactBootstrap/>
			<BasicExample/>
		</div>
	);
}

export default App;
~~~

---
## Material UI

Veamos como podemos utilizar ***Material UI*** en un proyecto de utilizarlo:
### 1. Instalación de framework en proyecto.

Para utilizar el ***framework*** de ***Material UI*** es necesario instalarlo en nuestro proyecto:

~~~
npm install @mui/material @emotion/react @emotion/styled
~~~

~~~
npm install @fontsource/roboto
~~~

~~~
npm install @mui/material @mui/styled-engine-sc styled-components
~~~

Si deseamos utilizar también los ***iconos*** que ofrece ***Material UI***, debemos instalar también la librería de estas:

~~~
npm install @mui/icons-material
~~~

***Nota:*** Se recomienda visualizar la ***documentación oficial*** por si existe algun cambio.

***Nota:*** Podemos visualizar la ***instalación*** dentro de nuestro archivo `package.json`.

Con valores similares a:

~~~json
	"@fontsource/roboto": "^5.1.1",
	"@mui/icons-material": "^6.3.0",
	"@mui/material": "^6.3.0",
	"@mui/styled-engine-sc": "^6.3.0",
~~~

### 2. Utilización de componentes Material UI.

con todo esto, puedes utilizar cualquier componente dado dentro de ***Material UI***.

Veamos un ejemplo de un componente:

~~~jsx
import * as React from 'react';
import { styled, useTheme } from '@mui/material/styles';
import Box from '@mui/material/Box';
import Drawer from '@mui/material/Drawer';
import CssBaseline from '@mui/material/CssBaseline';
import MuiAppBar from '@mui/material/AppBar';
import Toolbar from '@mui/material/Toolbar';
import List from '@mui/material/List';
import Typography from '@mui/material/Typography';
import Divider from '@mui/material/Divider';
import IconButton from '@mui/material/IconButton';
import MenuIcon from '@mui/icons-material/Menu';
import ChevronLeftIcon from '@mui/icons-material/ChevronLeft';
import ChevronRightIcon from '@mui/icons-material/ChevronRight';
import ListItem from '@mui/material/ListItem';
import ListItemButton from '@mui/material/ListItemButton';
import ListItemIcon from '@mui/material/ListItemIcon';
import ListItemText from '@mui/material/ListItemText';
import InboxIcon from '@mui/icons-material/MoveToInbox';
import MailIcon from '@mui/icons-material/Mail';

const drawerWidth = 240;

const Main = styled('main', { shouldForwardProp: (prop) => prop !== 'open' })(

  ({ theme }) => ({

    flexGrow: 1,

    padding: theme.spacing(3),

    transition: theme.transitions.create('margin', {

      easing: theme.transitions.easing.sharp,

      duration: theme.transitions.duration.leavingScreen,

    }),

    marginLeft: `-${drawerWidth}px`,

    variants: [

      {

        props: ({ open }) => open,

        style: {

          transition: theme.transitions.create('margin', {

            easing: theme.transitions.easing.easeOut,

            duration: theme.transitions.duration.enteringScreen,

          }),

          marginLeft: 0,

        },

      },

    ],

  }),

);

  

const AppBar = styled(MuiAppBar, {

  shouldForwardProp: (prop) => prop !== 'open',

})(({ theme }) => ({

  transition: theme.transitions.create(['margin', 'width'], {

    easing: theme.transitions.easing.sharp,

    duration: theme.transitions.duration.leavingScreen,

  }),

  variants: [

    {

      props: ({ open }) => open,

      style: {

        width: `calc(100% - ${drawerWidth}px)`,

        marginLeft: `${drawerWidth}px`,

        transition: theme.transitions.create(['margin', 'width'], {

          easing: theme.transitions.easing.easeOut,

          duration: theme.transitions.duration.enteringScreen,

        }),

      },

    },

  ],

}));

  

const DrawerHeader = styled('div')(({ theme }) => ({

  display: 'flex',

  alignItems: 'center',

  padding: theme.spacing(0, 1),

  // necessary for content to be below app bar

  ...theme.mixins.toolbar,

  justifyContent: 'flex-end',

}));

  

export default function PersistentDrawerLeft() {

  const theme = useTheme();

  const [open, setOpen] = React.useState(false);

  

  const handleDrawerOpen = () => {

    setOpen(true);

  };

  

  const handleDrawerClose = () => {

    setOpen(false);

  };

  

  return (

    <Box sx={{ display: 'flex' }}>

      <CssBaseline />

      <AppBar position="fixed" open={open}>

        <Toolbar>

          <IconButton

            color="inherit"

            aria-label="open drawer"

            onClick={handleDrawerOpen}

            edge="start"

            sx={[

              {

                mr: 2,

              },

              open && { display: 'none' },

            ]}

          >

            <MenuIcon />

          </IconButton>

          <Typography variant="h6" noWrap component="div">

            Persistent drawer

          </Typography>

        </Toolbar>

      </AppBar>

      <Drawer

        sx={{

          width: drawerWidth,

          flexShrink: 0,

          '& .MuiDrawer-paper': {

            width: drawerWidth,

            boxSizing: 'border-box',

          },

        }}

        variant="persistent"

        anchor="left"

        open={open}

      >

        <DrawerHeader>

          <IconButton onClick={handleDrawerClose}>

            {theme.direction === 'ltr' ? <ChevronLeftIcon /> : <ChevronRightIcon />}

          </IconButton>

        </DrawerHeader>

        <Divider />

        <List>

          {['Inbox', 'Starred', 'Send email', 'Drafts'].map((text, index) => (

            <ListItem key={text} disablePadding>

              <ListItemButton>

                <ListItemIcon>

                  {index % 2 === 0 ? <InboxIcon /> : <MailIcon />}

                </ListItemIcon>

                <ListItemText primary={text} />

              </ListItemButton>

            </ListItem>

          ))}

        </List>

        <Divider />

        <List>

          {['All mail', 'Trash', 'Spam'].map((text, index) => (

            <ListItem key={text} disablePadding>

              <ListItemButton>

                <ListItemIcon>

                  {index % 2 === 0 ? <InboxIcon /> : <MailIcon />}

                </ListItemIcon>

                <ListItemText primary={text} />

              </ListItemButton>

            </ListItem>

          ))}

        </List>

      </Drawer>

      <Main open={open}>

        <DrawerHeader />

      </Main>

    </Box>

  );

}
~~~

***¡Intenta importar este componente y otros más!***

