# **Standard Operating Procedure (SOP): Respiratory Effort Recording**

## **Before the Participant Arrives**

Gather the following equipment:

- BIOPAC Respiratory Effort Transducer (SS5LB)

### **Respiration Belt Setup**

1. Run the strap through the side buckles on the transducer, ensuring the self-adhering (Velcro style) side of the strap is facing upward.  
2. Flip the tip of the strap back over the buckle so it adheres to the rest of the belt (see Fig. 1).  

<p align="center">
  <img src="../images/Respiratory_Fig1.png" alt="Respiratory transducer strap" width="60%">
  <br>
  <em>Figure 1. Strap threaded through respiratory effort transducer buckle.</em>
</p>

### **Open Recording File**

If a template recording file for your experiment exists:  
**Open Biopac → Open graph file from disk → `template.gtl`**

If this is the first time setting up:  
**Open Biopac → Create empty graph**
In the toolbar at the top of the application click MP36 → Set Up Channels...
Ensure the correct recording channel is selected
In the top right corner, click Setup and → ensure that the aquisition time is set long enough for your session. If it isnt, Biopac will stop recording before your experiment is complete.

---

## **Upon Participant Arrival**

### **Participant Briefing and Consent**

- Welcome the participant and explain the procedure.  
- Ensure the participant understands the procedure.  
- Obtain verbal consent from the participant.

---

### **Respiration Belt Placement**

1. Ask the participant to stand and hold the transucer in the centre of their chest (over their clothes) and turn to face away from you
2. Thread the loose end through the plastic loop
3. Instruct the participant to **exhale completely** and tighten the belt around the chest/abdomen.  
   - The belt should not be loose at the point of complete exhalation.  
4. Ask the participant to **inhale fully** and adjust the tightness so that they feel a **slight resistance** when their lungs are full.

<p align="center">
  <img src="../images/Respiratory_Fig2.png" alt="Respiratory belt placement" width="60%">
  <br>
  <em>Figure 2. Participant positioning the respiratory belt on the chest/abdomen.</em>
</p>

6. Ask the participant to sit in the provided chair for recording.

---

## **Starting the Recording**

### **Start Recording**

- Press **“Start Recording”** on the Biopac system.  
- Verify that the live respiratory signal appears as expected (see Fig. X).
- If you cannot see a clear signal, the belt may need to be tightened.

> **Helpful Hints**  
> <details>
> <summary>Click to expand</summary>
> - You may struggle to see a clear signal if the recording is too short or the data channel is zoomed in too much.  
> - Allow the data to be collected for at least 15 seconds, then right-click and choose “See All Data” to rescale the waveform and get a better view.
> </details>

---

## **Post-Recording Procedure and Data Processing**

### **1. Stop the Recording**

- Press **“Stop”** on the Biopac system.

---

### **2. Remove Respiration Belt **

- Instruct the participant to detach the Velcro strap and remove the respiratory belt.  
---

### **3. Filter and Save Data**

1. Save the unprocessed file using a clear, descriptive filename (e.g., `participantID_raw`).  
2. Apply filters by navigating to:  
   **Transform → Digital Filter → IIR → Low**  
   - Set **Low cutoff:** 1 Hz  
3. Save the processed file using a clear, descriptive filename (e.g., `participantID_filtered`).

---

### **Post-Measurement Cleanup**

- Store the respiratory belt according to lab protocol.  
