# Omnitrix
A website on OMNITRIX watch
1. Project Setup

Created an HTML document with a structured layout including <head>, <style>, and <body> tags.

Added metadata for character encoding and responsive design.

2. Styling the Page

Defined a consistent dark sci-fi theme using CSS variables and gradients.

Styled the background with a layered radial and linear gradient to simulate a night-tech atmosphere.

Created a central title (OMNITRIX) with glowing green effects.

3. Layout Components

Created a .container div to hold all Omnitrix and alien icons.

Added a central .omnitrix button styled with a circular image and hover scaling.

Added 10 .alien divs representing selectable alien transformations, placed in a circle.

Added an .alien-details-container to display pop-up info on selected aliens.

Added an .ben10-info-box to describe the Ben 10 concept.

4. JavaScript Functionality

Defined an array aliens for alien image filenames and alienDetails for their names and descriptions.

Initialized an omnitrixDetails object for Omnitrix info.

5. Positioning Alien Icons

Used positionAliens() function to distribute 10 alien icons evenly in a circle around the Omnitrix using trigonometry (sine and cosine).

6. Animation (Rotation Effect)

Implemented rotateAliens() function with setInterval() to rotate aliens in a circular orbit continuously.

7. Interaction

Added onclick to Omnitrix and alien icons to trigger pop-ups with relevant images and text.

showOmnitrixDetails() shows details of the Omnitrix in a styled modal box.

showAlienDetails(index) displays corresponding alien info.

closeAlienDetails() hides the modal box.

8. Initialization

Called positionAliens() and rotateAliens() on load to render the interface and start the animation.

Conclusion:
This web app recreates a Ben 10 Omnitrix-style interface with interactive transformations and visually engaging animations using HTML, CSS, and JavaScript.

