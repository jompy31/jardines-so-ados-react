# Jardines Soñados

Jardines Soñados is a professional landscaping service offering high-quality solutions for garden care. We specialize in transforming outdoor spaces with attention to detail and dedication. Our team ensures that your garden looks vibrant and healthy year-round.

**Website:** [Jardines Soñados](https://jardines-sonados.netlify.app/)

## Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Components](#components)
- [Installation](#installation)
- [Usage](#usage)
- [Contributing](#contributing)
- [License](#license)

## Overview

Jardines Soñados offers a user-friendly website where clients can learn about our services and get in touch with us for landscaping solutions. The website includes sections for showcasing our services, client reviews, portfolio, and contact form for easy communication through WhatsApp.

## Features

- **Hero Section**: Introduces the company with a bold statement about professional landscaping and products.
- **Services Section**: Details the services offered, allowing users to explore landscaping solutions.
- **Client Reviews**: Showcases client feedback with visual elements like icons and text.
- **Contact Modal**: Enables users to contact the company directly through a WhatsApp message by filling in their name, phone number, and service description.
- **Responsive Design**: Fully responsive for both desktop and mobile users.

## Components

### `App.jsx`

<p>
This is the main entry point of the application, rendering all the components.
</p>
<code>
import Clients from "./components/Clients";
import Header from "./components/Header";
import Hero from "./components/Hero";
import Works from "./components/Works";
import Reviews from "./components/Reviews";
import Services from "./components/Services";
import Footer from "./components/Footer";

function App() {
  return (
    <div>
      <Header />
      <Hero />
      <Works />
      <Reviews />
      <Services />
      <Footer />
    </div>
  );
}

export default App;
</code>

### `Clients.jsx`

<p>
This component showcases the companies and brands that trust the services of Jardines Soñados. It includes logos from well-known companies like Google, Amazon, and Shopify.
</p>
<code>
const Clients = () => {
  return (
    <div className="bg-gray-100 p-8 flex flex-col items-center justify-center gap-8 mt-20 xl:mt-0">
      <h1 className="text-2xl font-medium text-gray-800 text-center">
        Con la confianza de las mejores empresas
      </h1>
      <div className="flex flex-col md:flex-row items-center flex-wrap gap-20">
        <img src="google.png" className="w-40" />
        <img src="airbnb.png" className="w-40" />
        <img src="amazon.png" className="w-40" />
        <img src="shopify.png" className="w-40" />
      </div>
    </div>
  );
};
</code>

### `ContactModal.jsx`

<p>
This component handles the contact modal, allowing users to send a message directly via WhatsApp. It includes fields for the user's name, phone number, and service description.
</p>
<code>
const ContactModal = ({ isOpen, onClose }) => {
  const [name, setName] = useState("");
  const [phone, setPhone] = useState("");
  const [serviceDescription, setServiceDescription] = useState("");

  const handleSend = () => {
    const message = `Hola, mi nombre es ${name}. Mi número de teléfono es ${phone}. Estoy interesado en el siguiente servicio: ${serviceDescription}.`;
    const whatsappUrl = `https://api.whatsapp.com/send?phone=50662558356&text=${encodeURIComponent(message)}`;
    window.open(whatsappUrl, "_blank");
    onClose();
  };

  if (!isOpen) return null;

  return (
    <div className="fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center">
      <div className="bg-white p-8 rounded-lg w-full max-w-md relative">
        <button
          className="absolute top-4 right-4 text-2xl font-bold text-gray-500 hover:text-gray-700"
          onClick={onClose}
        >
          &times;
        </button>
        <h2 className="text-2xl mb-4">Contáctanos</h2>
        <form className="flex flex-col gap-4">
          <input
            type="text"
            placeholder="Nombre"
            value={name}
            onChange={(e) => setName(e.target.value)}
            className="p-2 border rounded"
          />
          <input
            type="text"
            placeholder="Número de Teléfono"
            value={phone}
            onChange={(e) => setPhone(e.target.value)}
            className="p-2 border rounded"
          />
          <textarea
            placeholder="Descripción del Servicio"
            value={serviceDescription}
            onChange={(e) => setServiceDescription(e.target.value)}
            className="p-2 border rounded"
          />
          <button
            type="button"
            onClick={handleSend}
            className="bg-primary text-white py-2 px-4 rounded"
          >
            Enviar
          </button>
        </form>
      </div>
    </div>
  );
};
</code>

### `Header.jsx`

<p>
This component contains the header of the page, including a navigation menu that adapts to different screen sizes. It uses React Icons for the mobile menu actions.
</p>
<code>
const Header = () => {
  const [showMenu, setShowMenu] = useState(false);
  return (
    <header className="flex items-center justify-between xl:justify-start w-full py-4 px-8 h-[10vh] z-50">
      <div className="xl:w-1/6 text-center -mt-4">
        <a href="#" className="text-2xl font-bold relative p-1 bg-white">
          Jardines_Soñados<span className="text-primary text-5xl">.</span>
        </a>
      </div>
      <nav className={`fixed bg-white w-[80%] md:w-[40%] xl:w-full h-full ${showMenu ? "left-0" : "-left-full"} top-0 xl:static flex-1 flex flex-col xl:flex-row items-center justify-center gap-10 transition-all duration-500 z-50`}>
        <a href="#home" className="">Página Principal</a>
        <a href="#aboutUs" className="">Acerca de Nosotros</a>
        <a href="#services" className="">Servicios</a>
        <a href="#aboutUs" className="">Productos</a>
      </nav>
      <button
        onClick={() => setShowMenu(!showMenu)}
        className="xl:hidden text-2xl p-2"
      >
        {showMenu ? <RiCloseLine /> : <RiMenu3Fill />}
      </button>
    </header>
  );
};
</code>

### `Hero.jsx`

<p>
This component displays the main image of the site and an introductory message about the landscaping services offered. It also includes a button for contacting the team.
</p>
<code>
<section id="home" className="min-h-[90vh] grid grid-cols-1 xl:grid-cols-8">
  <div className="md:col-span-5 flex items-center justify-center p-8 xl:p-16">
    <div className="flex flex-col gap-8">
      <h1 className="text-5xl xl:text-7xl font-bold xl:leading-[7.5rem]">Jardinería Profesional</h1>
      <p className="text-gray-500 text-2xl leading-[2.5rem]">
        Ofrecemos soluciones integrales para el cuidado de tu jardín.
      </p>
      <div className="flex flex-col md:flex-row items-center gap-4">
        <button
          className="w-full xl:w-auto bg-primary text-white py-2 px-8 rounded-xl text-xl"
          onClick={openModal}
        >
          Contáctanos
        </button>
      </div>
    </div>
  </div>
</section>
</code>

## Installation

1. Clone this repository to your local machine:
    ```bash
    git clone https://github.com/tu-usuario/jardines-sonados.git
    ```

2. Navigate to the project directory:
    ```bash
    cd jardines-sonados
    ```

3. Install the dependencies:
    ```bash
    npm install
    ```

4. Run the development server:
    ```bash
    npm start
    ```

5. Access the application in your browser at [http://localhost:3000](http://localhost:3000).

## Contributing

If you want to contribute to this project, please open an issue or submit a pull request.
