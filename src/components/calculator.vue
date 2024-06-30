<template>
  <v-app>
    <v-container>
      <h1>Wave and Optics Calculator</h1>
      <v-row class="calculator-options">
        <v-col cols="6">
          <v-btn class="wave" @click="showCalculator('wave')">Wave Calculator</v-btn>
        </v-col>
        <v-col cols="6">
          <v-btn class="optics" @click="showCalculator('optics')">Optics Calculator</v-btn>
        </v-col>
      </v-row>

      <!-- Wave Calculator -->
      <v-row v-if="activeCalculator === 'wave'">
        <v-col cols="12">
          <v-card>
            <v-card-title>
              <h2>Wave Calculator</h2>
            </v-card-title>
            <v-card-text>
              <v-row>
                <v-col cols="6">
                  <v-text-field v-model="frequency" label="Frequency (Hz)" type="number"></v-text-field>
                </v-col>
                <v-col cols="6">
                  <v-text-field v-model="wavelength" label="Wavelength (m)" type="number"></v-text-field>
                </v-col>
              </v-row>
            </v-card-text>
            <v-card-actions>
  <v-btn class="calculate-wave" @click="calculateWave">Calculate</v-btn>
</v-card-actions>
            <v-card-text>
              <h2>Results:</h2>
              <p>Wave Speed: {{ waveSpeed }} m/s</p>
            </v-card-text>
            <v-card-text>
              <canvas id="waveGraph" ref="waveGraphCanvas"></canvas>
            </v-card-text>
          </v-card>
        </v-col>
      </v-row>

      <!-- Optics Calculator -->
      <v-row v-if="activeCalculator === 'optics'">
        <v-col cols="12">
          <v-card>
            <v-card-title>
              <h2>Optics Calculator</h2>
            </v-card-title>
            <v-card-text>
              <v-row>
                <v-col cols="6">
                  <v-text-field v-model="objectDistance" label="Object Distance (cm)" type="number"></v-text-field>
                </v-col>
                <v-col cols="6">
                  <v-text-field v-model="focalLength" label="Focal Length (cm)" type="number"></v-text-field>
                </v-col>
              </v-row>
            </v-card-text>
            <v-card-actions>
              <v-btn @click="calculateOptics">Calculate</v-btn>
            </v-card-actions>
            <v-card-text>
              <h2>Results:</h2>
              <p>Image Distance: {{ imageDistance }} cm</p>
            </v-card-text>
            <v-card-text>
              <canvas id="opticsGraph" ref="opticsGraphCanvas"></canvas>
            </v-card-text>
          </v-card>
        </v-col>
      </v-row>
       <!-- Report Section -->
      <v-row>
        <v-col cols="12">
          <v-card>
            <v-card-title>
              <h2>Wave and Optics Calculator: Physical Concepts and Technologies</h2>
            </v-card-title>
            <v-card-text>
              <h3>Introduction</h3>
              <p>
                The Wave and Optics Calculator is a web application developed using Vue.js and Vuetify. This application allows users to calculate wave speed and image distance for waves and optics problems, respectively. The application is designed with an interactive user interface that includes text fields for input and graphical representations of the results. In this report, we will explore the physical concepts, calculations, and formulas involved in the Wave and Optics Calculator, as well as the technologies used to build this application.
              </p>
              <h3>Physical Concepts and Calculations</h3>
              <h4>Wave Calculator</h4>
              <h5>Physical Concepts</h5>
              <p>
                Waves are disturbances that transfer energy from one point to another without the transfer of matter. The main properties of waves include frequency, wavelength, and wave speed.
              </p>
              <ul>
                <li><strong>Frequency (f):</strong> The number of wave cycles that pass a point per unit of time, measured in Hertz (Hz).</li>
                <li><strong>Wavelength (λ):</strong> The distance between successive crests or troughs of a wave, measured in meters (m).</li>
                <li><strong>Wave Speed (v):</strong> The speed at which the wave propagates through a medium, measured in meters per second (m/s).</li>
              </ul>
              <p>The relationship between these properties is given by the wave equation:</p>
              <p><strong>v = f · λ</strong></p>
              <h5>Calculation</h5>
              <p>
                The calculator takes the frequency and wavelength as inputs, validates them, and then calculates the wave speed using the formula mentioned above.
              </p>
              <ul>
                <li><strong>Frequency (f):</strong> User input in Hz.</li>
                <li><strong>Wavelength (λ):</strong> User input in meters.</li>
                <li><strong>Wave Speed (v):</strong> Calculated using <em>v = f · λ</em>.</li>
              </ul>
              <p>
                For example, if a user inputs a frequency of 10 Hz and a wavelength of 2 meters, the wave speed is calculated as:
              </p>
              <p><strong>v = 10 Hz × 2 m = 20 m/s</strong></p>
              <h5>Graphical Representation</h5>
              <p>
                The wave calculator also provides a visual representation of the wave. It plots a sinusoidal wave on a canvas element using the calculated properties. The wave's amplitude and number of cycles are dynamically adjusted to fit the canvas dimensions.
              </p>
              <h4>Optics Calculator</h4>
              <h5>Physical Concepts</h5>
              <p>
                Optics is the branch of physics that deals with the behavior and properties of light. Key concepts in optics include object distance, focal length, and image distance, particularly in the context of lenses.
              </p>
              <ul>
                <li><strong>Object Distance (d_o):</strong> The distance from the object to the lens.</li>
                <li><strong>Focal Length (f):</strong> The distance from the lens to its focal point.</li>
                <li><strong>Image Distance (d_i):</strong> The distance from the image to the lens.</li>
              </ul>
              <p>The relationship between these quantities is given by the lens formula:</p>
              <p><strong>\(\frac{1}{f} = \frac{1}{d_o} + \frac{1}{d_i}\)</strong></p>
              <p>Rearranging this formula to solve for image distance gives:</p>
              <p><strong>d_i = \(\frac{f · d_o}{d_o - f}\)</strong></p>
              <h5>Calculation</h5>
              <p>
                The calculator takes the object distance and focal length as inputs, validates them, and then calculates the image distance using the lens formula.
              </p>
              <ul>
                <li><strong>Object Distance (d_o):</strong> User input in centimeters.</li>
                <li><strong>Focal Length (f):</strong> User input in centimeters.</li>
                <li><strong>Image Distance (d_i):</strong> Calculated using <em>d_i = \(\frac{f · d_o}{d_o - f}\)</em>.</li>
              </ul>
              <p>
                For instance, if a user inputs an object distance of 30 cm and a focal length of 10 cm, the image distance is calculated as:
              </p>
              <p><strong>d_i = \(\frac{10 cm × 30 cm}{30 cm - 10 cm} = \frac{300 cm²}{20 cm} = 15 cm\)</strong></p>
              <h5>Graphical Representation</h5>
              <p>
                The optics calculator also provides a visual representation of the optical setup. It plots the object, lens, and image on a canvas element. The positions of the object and image are dynamically adjusted based on the calculated distances.
              </p>
              <h3>Technologies and Libraries Used</h3>
              <h4>Vue.js</h4>
              <p>
                Vue.js is a progressive JavaScript framework used for building user interfaces. It is known for its simplicity and flexibility. Vue.js allows for the creation of components, which are reusable instances with their own logic and templates. In this application, Vue.js is used to manage the user interface and application logic, including handling user inputs and displaying results.
              </p>
              <ul>
                <li><strong>Components:</strong> The application is structured into components, such as <code>&lt;v-app&gt;</code>, <code>&lt;v-container&gt;</code>, <code>&lt;v-row&gt;</code>, and <code>&lt;v-col&gt;</code>.</li>
                <li><strong>Data Binding:</strong> Vue.js provides two-way data binding, ensuring that the view updates automatically when the data changes.</li>
                <li><strong>Event Handling:</strong> Methods are defined in the Vue.js component to handle user events, such as button clicks for calculations.</li>
              </ul>
              <h4>Vuetify</h4>
              <p>
                Vuetify is a Vue.js framework that provides a collection of UI components following the Material Design specification. It enhances the visual appearance and usability of the application.
              </p>
              <ul>
                <li><strong>UI Components:</strong> Vuetify provides a wide range of pre-designed UI components, such as buttons, text fields, cards, and containers, used in this application.</li>
                <li><strong>Responsive Design:</strong> Vuetify components are responsive, ensuring the application looks good on various devices.</li>
              </ul>
              <h4>Canvas API</h4>
              <p>
                The Canvas API is used for drawing graphics via JavaScript. In this application, the Canvas API is utilized to create dynamic graphs for wave and optics calculations.
              </p>
              <ul>
                <li><strong>2D Context:</strong> The <code>getContext('2d')</code> method provides the 2D rendering context for drawing on the canvas.</li>
              </ul>
              <h3>Conclusion</h3>
              <p>
                The Wave and Optics Calculator is a powerful tool that combines the principles of wave physics and optics with modern web technologies. By leveraging Vue.js and Vuetify, the application provides an intuitive and interactive interface for users to calculate and visualize wave speed and image distance. The Canvas API enhances the user experience by providing dynamic graphical representations of the calculations. This application not only serves as a useful educational tool but also demonstrates the seamless integration of physics and technology in solving real-world problems.
              </p>
            </v-card-text>
          </v-card>
        </v-col>
      </v-row>
    </v-container>
  </v-app>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      activeCalculator: 'wave',
      frequency: null,
      wavelength: null,
      waveSpeed: null,
      objectDistance: null,
      focalLength: null,
      imageDistance: null
    };
  },
  methods: {
    showCalculator(type) {
      this.activeCalculator = type;
    },
    calculateWave() {
      const frequency = parseFloat(this.frequency);
      const wavelength = parseFloat(this.wavelength);

      if (isNaN(frequency) || isNaN(wavelength) || frequency <= 0 || wavelength <= 0) {
        alert("Please enter valid positive numbers for frequency and wavelength.");
        return;
      }

      this.waveSpeed = frequency * wavelength;
      this.drawWaveGraph(frequency, wavelength);
    },
    drawWaveGraph(frequency, wavelength) {
      const canvas = this.$refs.waveGraphCanvas;
      const ctx = canvas.getContext('2d');

      canvas.width = 600;
      canvas.height = 400;
      ctx.clearRect(0, 0, canvas.width, canvas.height);

      // Set background color to white
      ctx.fillStyle = 'white';
      ctx.fillRect(0, 0, canvas.width, canvas.height);

      // Draw axes
      ctx.beginPath();
      ctx.moveTo(50, 200);
      ctx.lineTo(550, 200); // X-axis
      ctx.moveTo(50, 50);
      ctx.lineTo(50, 350); // Y-axis
      ctx.strokeStyle = 'black';
      ctx.stroke();

      // Draw the wave
      ctx.beginPath();
      ctx.strokeStyle = 'blue';
      ctx.lineWidth = 2;

      // Calculate wave properties dynamically based on input values
      const amplitude = canvas.height / 4; // Adjust amplitude based on canvas height
      const cycles = 5; // Number of cycles to draw
      const period = wavelength * (canvas.width - 100) / (wavelength * cycles);

      for (let x = 0; x <= canvas.width - 100; x++) {
        const y = 200 + amplitude * Math.sin((2 * Math.PI * x) / period);
        ctx.lineTo(x + 50, y);
      }

      ctx.stroke();

      // Draw measurements
      ctx.font = "14px Arial";
      ctx.fillStyle = "black";
      ctx.fillText("0", 45, 215);
      ctx.fillText("X", 545, 215);
      ctx.fillText("Y", 35, 55);

      // Draw scale markings on X-axis
      for (let i = 0; i <= 5; i++) {
        ctx.moveTo(50 + i * 100, 195);
        ctx.lineTo(50 + i * 100, 205);
        ctx.fillText(i, 45 + i * 100, 215);
      }

      // Draw scale markings on Y-axis
      for (let i = -2; i <= 2; i++) {
        ctx.moveTo(45, 200 + i * 50);
        ctx.lineTo(55, 200 + i * 50);
        ctx.fillText(i * amplitude, 15, 205 + i * 50);
      }

      ctx.stroke();
    },
    calculateOptics() {
      const objectDistance = parseFloat(this.objectDistance);
      const focalLength = parseFloat(this.focalLength);

      if (isNaN(objectDistance) || isNaN(focalLength) || objectDistance <= 0 || focalLength <= 0) {
        alert("Please enter valid positive numbers for object distance and focal length.");
        return;
      }

      this.imageDistance = (focalLength * objectDistance) / (objectDistance - focalLength);
      this.drawOpticsGraph(objectDistance, focalLength, this.imageDistance);
    },
    drawOpticsGraph(objectDistance, focalLength, imageDistance) {
      const canvas = this.$refs.opticsGraphCanvas;
      const ctx = canvas.getContext('2d');

      canvas.width = 600;
      canvas.height = 400;
      ctx.clearRect(0, 0, canvas.width, canvas.height);

      // Set background color to white
      ctx.fillStyle = 'white';
      ctx.fillRect(0, 0, canvas.width, canvas.height);

      // Draw optical axis
      ctx.beginPath();
      ctx.moveTo(50, 200);
      ctx.lineTo(550, 200); // Optical axis
      ctx.strokeStyle = 'black';
      ctx.stroke();

      // Draw lens
      ctx.beginPath();
      ctx.moveTo(300, 100);
      ctx.lineTo(300, 300);
      ctx.strokeStyle = 'green';
      ctx.lineWidth = 4;
      ctx.stroke();

      // Draw object
      ctx.beginPath();
      ctx.moveTo(300 - objectDistance, 200);
      ctx.lineTo(300 - objectDistance, 100);
      ctx.strokeStyle = 'red';
      ctx.lineWidth = 2;
      ctx.stroke();
      ctx.fillText('Object', 300 - objectDistance - 20, 90);

      // Draw image
      ctx.beginPath();
      ctx.moveTo(300 + imageDistance, 200);
      ctx.lineTo(300 + imageDistance, 300);
      ctx.strokeStyle = 'blue';
      ctx.lineWidth = 2;
      ctx.stroke();
      ctx.fillText('Image', 300 + imageDistance - 10, 320);

      // Draw focal points
      ctx.beginPath();
      ctx.arc(300 + focalLength, 200, 5, 0, 2 * Math.PI);
      ctx.arc(300 - focalLength, 200, 5, 0, 2 * Math.PI);
      ctx.fillStyle = 'black';
      ctx.fill();
      ctx.fillText('F', 300 + focalLength - 10, 220);
      ctx.fillText('F', 300 - focalLength - 10, 220);
    }
  }
};
</script>

<style scoped>
.calculator-options button.wave {
    background-color: rgb(125, 72, 125);
}

.calculator-options button.wave:hover {
    background-color: rgb(66, 46, 66);
}

.calculator-options button.optics {
    background-color: rgb(41, 97, 97);
}

.calculator-options button.optics:hover {
    background-color: rgb(36, 67, 67);
}
.calculate-wave {
  background-color: rgb(255, 140, 0); /* Orange color */
  color: white;
}
.calculate-wave:hover {
  background-color: rgb(255, 165, 0); /* Lighter orange color */
}
</style>
