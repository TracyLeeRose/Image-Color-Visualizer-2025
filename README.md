# Image Color Space Analyzer

Visualize the colors of any image as a 3D point cloud within the RGB color space using Three.js.

**(Optional: Insert a Screenshot or GIF of the analyzer in action here)**
*A visual like this would be highly recommended!*

## What it Does

This web application takes an image file you upload and plots every single pixel as a point in a 3D space.

*   The **X-axis** represents the **Red** value (0-255).
*   The **Y-axis** represents the **Green** value (0-255).
*   The **Z-axis** represents the **Blue** value (0-255).

Each point in the 3D cloud is colored exactly like the pixel it represents. This allows you to visually inspect the distribution and clustering of colors within your image.

## Features

*   **Image Upload:** Load common image formats (JPG, PNG, GIF, etc.).
*   **3D Visualization:** Renders an interactive 3D scatter plot using **Three.js**.
*   **RGB Point Cloud:** Each pixel becomes a colored point at its corresponding (R, G, B) coordinate.
*   **Labeled Axes:** Clear Red, Green, and Blue axes with numerical labels (0-255).
*   **Interactive Rotation:** Click and drag the mouse on the plot to rotate the view freely.
*   **Automatic Rotation:** Toggle automatic tumbling rotation on/off.
*   **Axis-Focused Views:** Buttons to orient the view to look primarily along the Red, Green, or Blue axis.

## How to Use

1.  **Open:** Simply open the `index.html` file in your web browser.
2.  **Upload:** Click the "Choose File" button and select an image file from your computer.
3.  **View:** An image preview will appear, and the 3D plot will generate below it, showing the color distribution.
4.  **Interact:**
    *   **Click and Drag:** Rotate the 3D point cloud.
    *   **Start/Stop Rotation Button:** Toggle the automatic tumbling animation.
    *   **R / G / B Buttons:** Click these to orient the view for a better perspective along the selected color axis. The scene will rotate *around* the chosen axis. For example, clicking 'R' will rotate the scene around the Y-axis, making it easier to see the spread along Red.

## How It Works (Briefly)

1.  The browser reads the selected image file.
2.  The image is drawn onto an invisible HTML `<canvas>`.
3.  The pixel data (RGBA values for every pixel) is extracted from the canvas using `getImageData()`.
4.  For each pixel:
    *   The R, G, and B values (0-255) are mapped to X, Y, and Z coordinates in the 3D space. (Specifically, `coord = (value - 127.5) / 2.55` to center and scale the data).
    *   The R, G, B values are also used to set the color of the corresponding point.
5.  Three.js is used to:
    *   Create the 3D scene, camera, and renderer.
    *   Draw the X, Y, Z axes and their labels.
    *   Create a `THREE.Points` object using the calculated positions and colors.
    *   Handle rendering, lighting, and user interactions (mouse drag, button clicks).

## Running Locally

1.  Clone this repository or download the `index.html` file.
2.  Open the `index.html` file in a modern web browser.

**Note:** An internet connection is required the first time you load the page (or after clearing cache) as it fetches the Three.js library from a CDN.

## Dependencies

*   **[Three.js](https://threejs.org/)**: JavaScript 3D library (loaded via CDN).

## License

*(Optional: Add your preferred open-source license here, e.g., MIT License)*
This project is provided as-is. Feel free to use, modify, and learn from the code.
