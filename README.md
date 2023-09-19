# ☑️ OPENLANE ☑️

## ABOUT THE REPOSITORY
OpenLane is an automated RTL to GDSII flow based on several components including OpenROAD, Yosys, Magic, Netgen, CVC, SPEF-Extractor, KLayout and a number of custom scripts for design exploration and optimization. The flow performs all ASIC implementation steps from RTL all the way down to GDSII.

You can check out the documentation, including in-depth guides and reference manuals at [ReadTheDocs](https://openlane.readthedocs.io/).


<img src="https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/b7591af9-cd28-4e59-abd4-c6a487935097" width=800 >



 # COURSE 
<details>
<summary> DAY 1 : Insecption of open-source EDA, Openlane and sky130pdk  </summary>
<br>

# 1) Introduction to QFN-48 Package,chip,pads,core,die,and IP's and Introduction to RISC-V

- Generally an Aurdino board or an FPGA board consists of an chip or processor inside it.
- The internal veiw of chip will be as below

![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/e360670e-f8d1-4ad0-89c5-5610e73a73e6)


![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/903374bb-7f68-429a-868f-f87c228b0d3c)


RISC-V is an open standard instruction set architecture based on established reduced instruction set computer principles. Unlike most other ISA designs, RISC-V is provided under royalty-free open-source licenses. 


![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/f911d452-d9a4-4226-976b-342f1c638536)





# 2) SOC Design and OpenLANE

## a) Components of open-source digital asic design**
 - Digital ASIC design, It mainly consists of
   - RTL IP's
   - EDA Tools
   - PDK Data

![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/aa667615-e543-40ba-adbd-77f215cb9ccf)
      

  - Open source digital ASIC design

![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/e8cdc897-6abe-422d-9e22-77ebbcf20177)

- What is PDK..?
  - Process Design Kit (PDK) Collection of files used to model a fabrication process for the EDA tools used to design an IC.
      - Process design rules : DRC,LVX,PEX
      - Device models
      - Digital standard cell Libraries
      - I/O libraries


 
## b) Simplified RTL2GDS Flow**

![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/3009c334-659e-4d09-89da-0314b20ba1db)

         1. Synthesis
         2. Floor planning and Power planning
         3. Placement 
         4. Clock tree synthsis (CTS)
         5. Routing 
         6. Sign off



## c) Introduction to Openlane ans strivechipsets**

   #### OPENLANE was started as an open-souce flow for a true Open source Tape-out experiment,
   #### STRIVES is a family of open everything socs.

   ![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/112a893f-0072-4018-88fa-10d6b07258ce)


   #### Goal of Openlane asic flow is :
    - Produce a clean GDSII with no humaninterventions
         - CLEAN means 
                - No LVS voilations
                - No DRC voilations
                - Timming voilations

    - Open Lane is tunned for the skywater 130nm open PDK .
    - Open lane is containerzied which means
                - Functional out of the box 
                - Instruction to built and run natevly with flow
    - Open lane has two mode of operation 
                - Atonomous 
                - Interative


## d) Introduction to Openlane Detailed ASIC flow design


   ![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/2d90d2e2-ba8a-48e9-bca7-b22d68195acc)

   
Here's a detailed ASIC design flow using OpenLane and the associated tools and software:

**1. Synthesis:** RTL code is synthesized into a gate-level netlist, optimizing for area, power, and timing.
   - **Tools/Software**: 
     - Yosys for synthesis.
     - ABC (A System for Sequential Synthesis and Verification) for technology mapping.
     - Cell libraries specific to the target process.
     - Yosys

       
**2. Floorplanning:** Define the chip's area and arrangement of major functional blocks.
   - **Tools/Software**: 
     - OpenROAD's TritonRoute for global placement.
     - Magic for floorplan visualization.
     - Chip floor planning - Partinioning the chip die between different system building blocks and place the I/O pads.
     - Macro floor planning - Dimensions, Pin locations, rows defination.
     - Power planning - It is typically assigned with multiple VDD and VSS (Power straps, Power pads, Power rings)
    
       
**3. Placement:** Position individual gates and standard cells optimally within the predefined areas.
   - **Tools/Software**: 
     - RePLace (REctangle PLACEr) for placement.
     - Magic for placement visualization.
     - Placement is usually done in 2 steps
              - Global placement
              - Detailed placement

       
**4. Clock Tree Synthesis:** Design a clock distribution network to ensure synchronous clock signals.
   - **Tools/Software**: 
     - OpenROAD's TritonCTS for clock tree synthesis.
    
     
**5. Routing:** Establish interconnections while adhering to design rules, optimizing for signal integrity and timing.
   - **Tools/Software**: 
     - FastRoute for global and detailed routing.
     - Magic for routing visualization.


**6. Design Rule Checking (DRC):**  Verify that the layout complies with manufacturing design rules.
   - **Tools/Software**: 
     - Magic for initial DRC checks.
     - OpenROAD's TritonRoute for DRC repair.


**7. Layout Versus Schematic (LVS) Verification:** Confirm that the physical layout matches the intended functionality described at the RTL level.
   - **Tools/Software**: 
     - Netgen for LVS checks.


**8. Parasitic Extraction:** Extract parasitic capacitance and resistance values from the layout for accurate timing analysis.
   - **Tools/Software**: 
     - QFlow's SPEF extraction tool for parasitic extraction.


**9. Static Timing Analysis (STA):** Analyze timing paths to ensure setup and hold time constraints are met.
    - **Tools/Software**: 
      - OpenSTA for static timing analysis.


**10. Physical Verification:** Perform a series of checks including DRC, LVS, and electrical rule checks (ERC).
    - **Tools/Software**: 
      - Magic for DRC and LVS checks.
      - Netgen for ERC checks.


**11. GDS2 Generation:** Convert the final layout data into GDS2 format for fabrication.
    - **Tools/Software**: 
      - Magic for GDS2 generation.Here's a detailed ASIC design flow using OpenLane and the associated tools and software:



#### Synthis exporation
![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/cebdad09-b756-41b7-978a-5207cda487f2)


#### Design exploration
  ![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/7d1b82d0-c25e-499d-a499-b265da46197a)


# 3) Open- Source EDA tools

#### Openlane Directory structure in detail

   - cd Desktop/
   - cd home/tools/
   - cd openlane_working_dir/
   - ls
   - cd openlane
   - docker
   - ./flow.tcl -interactive

![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/c888176e-1f70-442f-9cf7-84e865898911)


#### Design Preparation step

    - in openlane directory
    - package require openlane 0.9
    - prep -design picorv32a

![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/cc01cf5a-a7d6-44b7-86a5-065977e2eafb)


#### Review files after design synthsis and run synthsis

    - run_synthesis

![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/0e4690bd-42b7-4824-96e3-c6879a5e5654)


![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/550268eb-a857-49bb-89ba-5a99a0ab0262)


   - Here the counter d flipflop is **1613**
   - The number of cells is **14876**
   - The flop ration for our design will be 1613/14876 = 0.108
   - In percentage = 10.08 %

     
#### Openlane Project Github link Discription

https://github.com/efabless/openlane

[Back to COURSE](https://github.com/Vinodkumar8318/Pes_Openlane_work/tree/main#course)

</details>




<details>
<summary>DAY 2 : Good floorplan vs bad floorplan and introduction to library cells </summary>
<br>


# GOOD FLOORPLAN VS BAD FLORPLAN AND INTRODUCTION TO LIBRARY CELLS

## 1) CHIP FLOOR PLANNING CONSIDERATIONS

## L1) Utilization Factor and Aspect ratio

  ![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/3aef58ab-6ea3-4aec-9ea3-a1c5ed63b771)

    - Defining the width and height of the core and Die
    - Consider a netlist with 2 FF and 2 gates with the connections shown below


**STEP-1** Make the gates as a Squared box 

![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/4f09822c-6af6-42c8-a712-5ae75beed286)


**STEP-2** Find out the dimensions of the core and Die ( Dimensions of the standard cells )

![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/3e2a0161-d1df-470b-a65f-0163083508ad)


 #### For example 
  - Let us assume that each FF and Gates is on 1 cm breadth and 1cm height
  - Now Area of each standard cell will be will of 1 cm sq .
  - Allining tha area ocuupied the netlist in a in a single core .
  - Below the netlist will be fit into the core So it will be **100% utilization**
  - **Utilization factor** = Area occupied by the netlist / Total area ocuupied by the core.
  - where 4sq / 4sq = 1 . 
  - In this case when utilization factor = 1 , then the core is full no extra components can be added.
  - **Aspect ratoio** = Height / width , if it is 1 , it signifies that the core is square shaped.




## L2) Pre placed cells

![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/a005bcbc-a546-4648-b8a5-0e23ad8c1944)

  - Conisder a combinational block -> Gate level diagram.
  - Seperate that gate level diagram into two blocks.
  - Consider the multiple blocks are inside a Black box Now seperate the blackbox as two differnet IP's or Modules .
  - The Arrangements of the IP's in a chip is called as **Floor planning**.
  - The IP's will have an user defined loctions and they can be placed in a chip before the placement and rouiting is done hence these are calle as **Pre placed Cells**




## L3) Decoupling Capacitors

![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/1892d647-2b21-4e6a-8030-66ce9364f7cc)

  - For any signal to be considered as a Logic 0 and Logic 1, It should be within the NM range ( Either NML or NMH )
  - The area between the NML and NMH is called undefined area
  - So in order to maintain the signal to be in the NML or NMh **Decoupling capacitors** are used.
  - Decoupling capacitors are mainly used to maintain the signal are not inside the undefined area.
    



## L4) Power Planning

![Screenshot from 2023-09-14 12-58-34](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/ff16ed45-9495-49a6-b260-d3d194323738)

  - Insted of using individual VDD and VSS for multiple cells in a Block.
  - Suppose if there are four cells in a Block , Each cell having seperate VDD and VSS are called as **Power Planning**




## L5) Pin placement and Logical cell placement Blockage

![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/71f697d9-472c-4e79-a502-2f7001500a86)

  - Here consider a 4 set of circuts with input, clk and output,
  - Considering all 4 circuits together and placing on a chip in such a way that INPUTS should be at one side and OUTPUT should be at one side which helps us to make the connections easily.
  - So this process is called as **Pin placement**
  - Making sure that non of the automated routing tool should not be placed near the i/p and o/p cells it needs to block the cells This is called as **Logical cell placement Blockage**
    

**Pin Placement**

![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/e9a4597c-0d8b-4c75-a8a2-051b0ecb81c7)


**Logical cell placement Blockage**

![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/cf98ef58-1fb1-4de8-9767-064c70428a9c)





## L6) Steps to run Flopor planning using Openlane

      - These are the defalt Floorplans 
 
 ![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/490bb702-b125-4a02-8b91-f3b190a4580b)


 ![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/7d421dc9-ea0c-4250-ae6f-2d8598717d3b)


 ![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/e080bb6a-bb17-4001-a3f2-0774536b20b4)


## L7)

              - In the openlane shell

![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/382fb424-a1f7-46a5-981d-bf0aef5ba065)
              
              - To open the Floorplan we go to the required directory that is
                   > vsduser@vsdsquadron:~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/11-09_15-36/results/floorplan
              - Using the ```cd``` command.
              - Then we type the command:
                   > magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.floorplan.def &

              - The following layout is displayed

![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/6622214d-dac3-4cd8-b8d2-f3f30c095247)

              - We can press 's' and then 'v' to align the design to the center of the screen.

              - We can right click on the mouse and pess 'z' to zoom into a desired part.

![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/8fb90206-cd3c-4177-9936-09885389bc84)

              - We can check the details of the ports as follows
              - Hover over a port with your crosshair and press 's' on your keyboard
              - Now open the tkcon command window and type ```what```.
              - This will show you the details of the selected port.

![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/fbb5a5da-ce91-41fa-a23b-21eda8b68d5c)
             
              - If we zoom in a little more, we can see the tap cells.
              - They are present to prevent latch up conditions which occur in the CMOS devices

![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/540cc442-61e7-41f9-8075-276feb7f048f)

              - These are the standard cells that are used in the design




## 2) LIBRARY BINDING AND PLACEMENTS


### L1) Netlist binding and initial Place Design

       - Bind netlist with physical cells 
       - Here it defines about the shape and sixe of the standard cell
       - Each cells are defined only in either rectange shape or square shape 
       - In this example, 1 refers to NOT gate, 2 refers to AND gate.   [image 1]
       - Larger the cell size 
          > It has a least resistance path
          > Performes Faster
       - Once we have a Physical veiw of all cells, It is placed on the Floorplan according to the Netlist.  [image 2]

![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/42d823d6-4c27-4631-805e-7d8d972ab95a)


![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/f7ff1136-48b7-4e0f-81ea-6a4cbeba3222)



### L2 and L3) Optimize placement using estimate wire length and capacitance

        - When the cells are not extactly placed on the floorplan as in the netlist, If the relevant cells are not near to i/p or o/p.
        - Then estimation of wirelength and capacitance comes in.
        - Depending on the Capacitance and how far the cells are from input and output, Some **Buffers** are added in order to reduce the Wirelength and also to get a complete signal without any             lossses of signal ( but in cost of Area which can be minimized later )
    
          
![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/59d2d9da-75ca-4615-88e4-f0c0c9878509)


![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/efe1ae28-f0bd-4df2-aec4-b2316b7e3857)



### L4) Need for libraries and characterization 

        - Library characterization and modelling depends on some steps,
        - Logic synthesis  ->  Floor planning  ->  Placement  ->  Clock Tree synthesuis ( CTS )  ->  Routing 
        - The collection of all the standard cells are placed is one area which is referred as **Library**

        
![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/2c0629b1-a07e-45d8-a58a-3e865f7ff28f)



### L5) Congestion aware placement using replace
          - To view the placement we type
                   > run_placement
          - In the OpenLANE shell.

![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/18162a42-f288-4007-baba-6f759a9a6184)

          - This is the result displayed. As we can see the '/picorv32a.placement.def' file is read.

![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/5c9dc6ed-fc8e-4f8f-80c8-922a4f749991)

          - We move one directory up from the 'floorplan' folder using
                   > cd ../placement/

          - To view the placement design we use the command
                   > magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.placement.def

![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/a2807440-c80b-43c3-967d-e2c113fb44a4)

          - The above is displayed.
          - All these standard cells were present at the initial layout of the floorplan.

![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/c4f005a1-0ac8-4693-bf09-d920692c4f09)

          - If we zoom in we can see the placement of the standard cells in the standard cell rows.




## 3) CELL DESIGN AND CHARACTERIZATION FLOW

### L1) Inputs for cell Design Flow
       - For each standard cell (AND,NOR,INVERTER,FF ect) There are different cell design flow
       - Each Cell Design Flow consists of 3 steps:
               - Inputs ( which mainly consists of PDK's [ DRC and LVs rules, Spice models, library ect] )
               - Design Steps (this mainly invovles 3 steps)
                      - Circuit Design
                      - Layout Design 
                      - Charecterization
               - Outputs ( Outputs we get here is  CDL circuit description language )
               
   #### User defined specifications
       - Cell height = The seperation between the power rail and ground rail defines the cell height.
       - Supply voltage = A certain cell should be operated at a certain supply voltage which is defined by the Top level design
       - Metal Layer = Certain Libraries van be designed on a particular Metal Layer.
       - Pin Location = Library nedds to decide on the pins and the pin location where it needs to be placed.

               
### L2) Circuit Design step
      - There are teo steps involved in circuit design:
            > Implement the Function itself
            > Modelling the PMOS and NMOS transisters in such a way that the aspect ratio should be matched.
            
      
### L3) Layout Design step
      - Implimenting the PMOS and NMOS values into layout are called Layout Design 
      - Steps involved in the layout design are:
           - Get the function implimented through the MOS transistors
           - Get a PMOS network graph and NMOS network graph
           - Obtain Euler's Path and draw a Stick Diagram
           - Convert the stick diagram into a proper Layout diagram
           - EXtract the paracetics from the layout and CHaracterize it interms of Timmings.

           
### L4) Typical Charaterization Flow
     - Steps involved in the characteriztion flow are :
           - Read in the Model Files
           - Read the extracted spice netlist
           - Define how to recongnise the behaviorur of the buffer
           - Read the subcircuits of the inverters 
           - Attach the neccessary Power source
           - Apply the stimulus
           - Provide the neccessary output capacitance
           - Provide the necessary simulation command.
           - Feed in all the 1 to 8 steps to a configuration file ( GUNA )


![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/0628a4c9-b6ec-4321-8d47-738c8892cd6a)


![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/0f0ba7e0-0b4c-4f67-87d7-b4256aaecca4)


![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/64a04551-d324-4641-ae5b-d285bfc35305)



## 4) GENERAL TIMMING CHARECTERIZATION PARAMETERS

### L1) Timming Threshold definations
      - Timming Threshold Definations
          - slew_low_rise_thr
          - slew_high_rise_thr
          - slew_low_fall_thr
          - slew_high_fall_thr
          - in_rise_thr
          - in_fall_thr
          - out_rise_thr
          - out_fall_thr

![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/785c4894-f56c-49f5-8967-64d8186ea5b3)


![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/7059e853-ae6d-4d3e-983d-6d60f1643bbe)


         
### L2) Propogation delay and transition time

**Propagation Delay**
The time difference between when the transitional input reaches 50% of its final value and when the output reaches 50% of its final value.
     
     - There should be no negative delay in the charecterization, This can be taken care by setting a proper threshold point.

```
    Propagation delay = time(out_fall_thr)-time(in_rise_thr)

```
![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/ad875fdb-f7fb-42e2-967e-307273173e1c)


![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/00e224cb-ad87-4d70-b4a5-ff520bede55d)


**Transition Time**
The time it takes the signal to move between states is the transition time , where the time is measured between 10% and 90% or 20% to 80% of the signal levels.

```
Rise transition time = time(slew_high_rise_thr) - time (slew_low_rise_thr)
```

```
Fall transition time = time(slew_high_fall_thr) - time (slew_low_fall_thr)
```

![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/0bc19251-9424-4e08-a7f4-c5fae5bc5072)



[Back to COURSE](https://github.com/Vinodkumar8318/Pes_Openlane_work/tree/main#course)

</details>
<details>
<summary>DAY 3: Design library cell using magic layout and ngspice characterization </summary>
<br>

# 1) LABS FOR CMOS INVERTER NGSPICE SIMULATIONS

   ### L1) IO Placer revision
   
   ### L2) Spice deck creation for CMOS inverter
             - Create a SPICE DECK first
             - > Connectivity information about the netlist
             - > Set a component values
             - > Identify the nodes
             - > Name the nodes


![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/954992d0-3bc7-4472-9da6-4d421e22b52b)


             SPICE DECK = ***Model description***
                          ***Netlist Description***
                          M1 out in vdd vdd pmos w=0.375u L=0.25u
                          M2 out in 0 0 nmos w=0.375u L=0.25u
                          
                          cload out 0 10f

                          Vdd vdd 0 2.5
                          Vin in 0 2.5
                          
                          *** Simulation commands ***
                          .op
                          .dc Vin0 0 2.5 0.05

                          *** .include tsmc_0.25um_model.mod ***
                          .LIB "tsmc_0.25um_model.mod" CMOS_MODELS
                          .end
                          
                          
![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/a0d82108-57f3-4a8e-b48d-738fd9455ed1)


![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/0da222fd-69e1-4669-b815-c301ba82f4d0)
 
   
   ### L3) Spice simulation lab for cmos inverter
                  - Spice simulation for a particular specification
                  
![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/6e63ed80-6cad-4f4a-9602-34ded2360357)


![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/d679273d-4f95-4d47-bab0-1246d5ffe000)


   ### L4) Switchin threshold vm
            - The CMOS on the right side has a bigger size than the one on the left.
            - These waveforms tell us that the CMOS is a very robust device. The characteristics of the CMOS are maintained across a variety of sizes.
            - The arrow is pointing to the point where 'Vin = Vout'.

![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/ceeebacd-4ae3-475b-af6e-d4e4570e9566)
            - Above graph gives details on each point and its significance
            
![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/8373d80c-5fe4-4bcf-b35f-c218f83439bb)


         - 
   ### L6) Lab steps to gitclone vsdstd cell design
            - We need to perform a git clone here from a repository that we require, to do the future labs.
            - We can type the following command
                  ```
                  git clone https://github.com/nickson-jose/vsdstdcelldesign.git
                  ```

            - Now we need to copy the 'sky130A.tech' file into the directory we just cloned
            - We can do this by using
                  ```
                  cp sky130A.tech /home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/vsdstdcelldesign
                  ```
                  ```
                  magic -T sky130A.tech sky130_inv.mag & 
                  ```  
             in the follwoing directory shown in the figure

![image](https://github.com/AniruddhaN2203/pes_pd/assets/142299140/c0cefbbc-dfd8-40b0-859e-3603e5589416)



  
## 2) INCEPTION OF LAYOUT CMOS FABRICATION PROCESS

### L1) Create Active Regions
           - Selecting a subsrate ( p-type, High resistivity, Doping level,oreintation )
           - Creating active region for transistors
                     - Step1 -> Deposit the kayer of photo resist
                     - Step2 -> Mask1 the region (protecting)
                     - Step3 -> So the UV rays doesnt hit the photoresist layer which is under Mask.
                     - Step4 -> Silicon layer is etched off in the Non masking region.
                     - Step5 -> Remove the Photoresist
                     - Step6 -> Placed in an oxidation furnance
                     - Step7 -> Isolation area will be created This process is called as LOCUS.

![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/bed3cb8f-55d9-43bb-900c-f99eff654df9)


![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/efe68587-e3f3-407b-ac55-4e7a50367459)


### L2) Formation of N-well and P-well
                   - Step1 -> Photoresist the Layer
                   - Step2 -> Mask2 in the required region
                   - Step3 -> Expose the photoresist to UV rays
                   - Step4 -> Non masking area will be wanished
                   - Step5 -> Create a P-well ,It is created by using BORON
                   - Step6 -> Create a N-well ,It is created by using Phosphorous
                   - Step7 -> Take the complete structure into High Temperature Furnace
                   - Step8 -> This diffuses the wells and make proper n-well and p-well, This is called as twin tub process

![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/d83b05f8-adc1-41d4-b455-bf37e3667804)


![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/e56c93fe-5afe-4ac4-b15e-887f9c99874d)


### L3) Formation of gate terminal
                   - Step1 -> Gate formation involves depositing a gate oxide
                   - Step2 -> Defining gate patterns using photolithography
                   - Step3 -> Depositing gate material
                   - Step4 -> Etching to create gates
                   - Step5 -> Doping the substrate and insulating the gates.

![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/52c6eeaa-9910-453b-b130-3cab4b728f1a)


![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/c37e64fa-802e-4db3-8bb0-55952be93be4)


### L4) Ligtly dopped drain (LDD) formation
                   - Lightly doped drain (LDD) formation involves implanting the drain and source regions of a MOSFET transistor with a lighter concentration of dopants to reduce hot 
                     electron effect and short channel effect and enhance device performance.
                   - Doing both  n+ impantation and p+ implantation.
                   - It involves plasma etching here
                   
 ![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/34f83ae3-dea6-4e6d-b049-46d2c3028048)


 ![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/62580c2e-af68-408f-8bfa-347d043ab5fe)

                            
### L5) Source and drain formation
                  - Source and drain formation in a MOSFET transistor typically involves doping the silicon substrate with chemicals such as arsenic or phosphorous for n-type regions 
                  (source and drain) and boron for p-type regions (source and drain).
                  - Here the source and drain are done by using ARSENIC method
                  - High temperature annealing is performed.

![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/79dd4508-6eca-4f86-bd6f-5c1240e692bf)


![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/3d2cc62f-0453-4712-9940-1b7215b5038d)


### L6) Local interconnect formation
                  - Steps to form Contacts and Interconnects(local) 
                      - Step1 -> Titanium is deposited with a process known as sputtering. 
                      - Step2 -> Wafer is heated to about 650 - 700 C in an N2 ambient furnace for 60 seconds. 
                      - Step3 -> TiSi2 contacts are formed.  TiN is also formed used for local communication. 
                      - Step4 -> TiN is etched using RCA cleaning.

![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/b1d69f8c-29cf-4d31-b1e0-28116431d9d5)


![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/9d82ed40-e8b0-4d33-ba28-4c4a654c5084)
                      
### L7) Higher level metal formation
                 - Step1 -> Forming contacts and interconnects locally involves depositing a dielectric material like silicon dioxide
                 - Step2 -> Patterning it using photolithography
                 - Step3 -> Eetching contact holes 
                 - Step4 -> Depositing a barrier metal (e.g., titanium or titanium nitride)
                 - Step5 -> Filling with a conductor (e.g., aluminum or copper) using chemical vapor deposition (CVD)
                 - Step6 -> And then planarizing through chemical-mechanical polishing (CMP).

![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/25b8dee5-80c4-4f95-983e-cf41e29050c4)


![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/0fe538d7-15d7-4334-b1ae-80112146cf3c)


![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/cdc36969-8abe-473b-bbea-7fbf91b0a7e2)


### L8) Lab introduction to Sky130 basic layers layout and LEF using inverter

                - Now let us look at the layout of a CMOS inverter. To open this we type the command

![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/ffaeccd3-bc9d-4169-a71c-bd49ac46d11f)

                - Now run the command 
                     > magic -T sky130A.tech sky130_inv.mag &
                - The following layout will be displayed.

![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/ff9195c0-7445-4f75-bf56-0e9d3567196d)


                - We can get to know the details of the inverter by hovering the mouse cursor over it and pressing 's' on the keyboard. 
                - Then we can type what in the tkcon. 
                - Pressing 's' three times will show what parts are connected to the selected part.
                - We shall look at the difference between LEF and Layout. The above image is a Layout.
                - LEF represents abstract component data in a machine-readable format for IC libraries, while layout is the physical geometric arrangement 
                  of these components on a semiconductor chip.


                 
### L9) Lab steps to create std cell layout and extract spice netlist

![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/2d94dc13-23e4-4fba-be19-c7b4ce650e60)


                - DRC error can be veiwed on the tkcon
                - To extract Spice Netlist we perform the following steps in the tkcon window:


![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/93bac30d-c8a1-4445-afed-ffe79c083150)



                - We use the commands
                       > ext2spice cthresh 0 rthresh 0 -> this is done to copy the parasitic capacitances
                - The next command is
                       > ext2spice
                - We can see that a sky130_inv.spice file will be created


![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/72bccd1d-53f6-4576-9d5e-1495bd6b2173)


## 3) SKY130 TECH FILE LABS

### L1) Lab steps to create final SPICE deck using Sky130 tech
               - To start off we look at the minimum value of the layout window

![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/3348cb27-20ec-41cd-8cb7-6ca935e4cf47)


               -  We can use 'g' on the keyboard to activate the grid and after selecting a grid by right clicking on the mouse, we type box in tkcon window to check the 
                  minimum value of the layout window


![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/e51c812f-17b3-4aec-9494-a7ca47789b0b)

### L2) Lab steps to characterize inverter using sky130 model files
               - Next we need to open the spice file using the command
                        > gedit sky130_inv.spice
               - We need to configure it to the above specifications.
               - Characterize Inverter using Sky130 Models
               
![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/47956882-ed55-49c0-b44d-c74b9b35bd90)

               - We now plot the graph for output vs input sweeping the time.
               - We first use the command
                        > ngspice sky130_inv.spice
               - In the ngspice shell we use the command
                        > plot y vs time a
               - The following graph will be displayed

![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/c84ab36b-f69f-4522-ae24-0e991cdcb186)


![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/15043af9-98b3-4240-9e95-3bab51d89998)


![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/7253702f-ef83-4dee-be43-8836d566c4fd)

#### Rise Time -> time taken to rise from 20% to 80% of the max value -> 2.25075e-09 - 2.184e-09 = 0.006675e-09 s.


![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/a2bbacc2-2fc3-4a0d-a479-83a7c0389344)


![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/0e30da76-0999-4ab1-a3f6-9f7984f4a64a)

#### Propogation Delay/Cell Rise Delay -> 2.21379e-09 - 2.15e-09 = 0.06379e-09 s.


### L3) Lab introduction to Sky130 pdk's and steps to download labs
               - Enter the command
                       > wget http://opencircuitdesign.com/open_pdks/archive/drc_tests.tgz
               - Move the fikes into the desktop using the below command
                       > mv drc_tests.tgz Desktop/
               - Extract the file using the folloeing command
                       > tar xfz drc_tests.tgz 
               - Check the files inside it using ls command

![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/a3efcb42-3468-44a8-ba79-b0a972615736)



![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/8a72b6d9-47e0-4232-be72-5e1cb4bc6610)
    
     
    
### L5) Lab introduction to Magic and steps to load Sky130 tech-rules

            - To open the software we type
                 > magic -d XR

![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/c5c111f9-de69-4615-852c-320067d29161)

![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/f1f51fc8-8a43-4ca4-8610-e834870977c3)

            - Selct M3 by clicking left an right button in the mouse , select an area M3
            - And then tpe this command in the tkcon window It shows a DRC error 
                 > drc why
                   
![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/7af2afdf-0c94-4a7a-9a54-0ee3b8fd16e5)

            - To add contact cuts to metal3, first select an area using left and right click. Then hovering 
                over the m3contact we click middle mouse button.
            - To check the black boxes inside this, Type the following command 
                 > cif see VIA2

![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/c2aee3f7-f35d-439b-a8c7-492aff5a56ba)



### L6) Lab exercise to fix poly.9 error in Sky130 tech-file
       - In magic file type the following command
            > load poly
       - There will a diff between the spacing of poly.9 
       - In order to over come this we need to sort the DRC error

![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/c1065d5c-547e-40c7-84e6-08c7689d1994)

       - There is a DRC error in the poly.mag file in 'poly.9'.
       - Open the sky130A.tech file in the editor and make the following changes
             > vi sky130A.tech 
       - Add this line in the editor 
             >  spacing xhrpoly,uhrpoly,xpc allpolynonres 480 touching_illegal \
                     "xhrpoly/uhrpoly resistor spacing to diffusion < %d (poly.9)"

             > spacing npres allpolynonres 480 touching_illegal \
                     "poly.resistor spacing to N-tap < %d (poly.9)"
              
![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/c1ea1ff1-9c76-44ba-b674-517ca947dcc6)

![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/8b6b7bc1-aa00-49ca-8a53-526dd57b0b5b)

      - Now open the tkcon window and type 
            > tech load sky130A.tech
            > drc check 
      - Now we can see that the DRC eroor will be solved 
      
![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/03a0b4ee-1598-4c77-b36c-3b104fe7c919)
  

### L8) Lab challenge exercise to describe DRC error as geometrical construct
      - Now we open the nmwell.mag file
      - Open the tkcon window and type the following command
           > cif ostyle drc
           > cif see dnwell_shrink
           > cif see nwell_missing
     - The following window appears

![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/4e033c6d-d5f7-4d5c-94af-cd5bff63ae19)


### L9) Lab challenge to find missing or incorrect rules and fix them
       - Add nsubstratencontact somwhere into the nwell

![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/bdda61a6-cdb9-4604-a666-ab2900f6e4a5)
      
       - And then make these changes in the editor file
          > cifmaxwidth nwell_untapped 0 bend_illegal \
              "Nwell missing tap (nwell.4)"

![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/b6cb691f-3c9c-4e1f-a57f-49a0d99f3961)

       - type the following commands in the editor file
          > templayer nwell_tapped
            bloat all nsc nwell
          > templayer nwell_untapped nwell
            and-not nwell_tapped
          
![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/13b35669-46d9-4629-a8f4-504bbb9bc8e6)

          > variants (full)
            cifmaxwidth nwell_untapped 0 bend_illegal \
              "Nwell missing tap (nwell.4)"
            variants *
            
![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/03fc9f68-758a-4258-a3ad-e49cb7d601d7)

      - Type the following commands in the tkcon window
            > tech load sky130A.tech
            > drc check
            > drc style drc(full)
            > drc check
      - The following window will appear

![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/344181e2-f267-4dc8-9c81-fa483c743b63)

      - Now if we select 'nsubstratencontact' somwhere inside the cell The problrm is solved
       
![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/d0590dd2-8681-4c1b-a4cd-3a2c95b719c9)




[Back to COURSE](https://github.com/Vinodkumar8318/Pes_Openlane_work/tree/main#course)

</details>
<details>
<summary>DAY 4 : Prelayout timming layout analysis and inportance of good clock tree </summary>
<br>

## 1) TIMMING MODELLING USING DELAY TABLES

### Lab challenge to find missing or incorrect rules and fix them

![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/7caa9c46-1f7b-4c44-a849-d023b7d3dba9)

       - Converting grid info into Track info
       - Go to openlane directory / sky130_fd_sc_hd 
       - type less tracks.info

![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/b5bde9d6-5d95-4452-aec7-138935f5cefb)


![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/be3f5c92-6ef6-4ab2-8493-078e2ca01cc6)

      - Here 1st value indicates the offset and 2nd value indicates the pitch along provided direction

 
 ### Setting grid values using above file info

        - ext2spice 
        - help grid
        - grid 0.46um 0.34um 0.23um 0.17um

![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/5a6ae931-fa7f-4dc5-9624-489a53ffe754)


### Before grid vs After grid

![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/7caa9c46-1f7b-4c44-a849-d023b7d3dba9)


![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/bec49fed-8a12-4cf5-ae15-cb9fb811da01)


![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/592a608a-8bed-4c5c-b0e2-7abe6cb3a418)

        - From the above pic, its confirmed that the pins A and Y are at the intersection of X and Y tracks. So the first condition is met.
        - The PR boundary is taking 3 grids on width and 9 grids on height which says that the 2nd condition is also met



## GENERATION OF A LEF FILE
        - Once the layout is perfect we can generate the lef file
        - In the tkcon window type the following command to save the updated layout
              > save sky130_vsdinv.mag
        - once it is saved then go to the terminal window and the type 
              > magic -T sky130A.Tech sky130_vsdinv.mag &
        - A magic layout opens , In the tkcon window type 
              > lef write

![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/f249106d-9204-4870-9122-1c2b5707cbf2)

        - Once this is done lef file should be created in the vsd file

![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/a969dff8-b8e6-45fd-9827-7938aaa223fb)

        - To open the lif file type the below command in the terminal
              > less sky130_vsdinv.lef

![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/8b5a5093-f378-4373-b4cf-43decea2ff80)


![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/63a7e1f5-e878-48a3-91d3-0430f89a5a85)


## STEPS TO INCLUDE NEW STEPS IN THE SYNTHESIS

        - Open the picorv32a pwd in the terminal
        - copy the path 

![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/59c7483e-40b2-4d23-b7c7-123fac3364c7)

        - Go to the vsdstdcelldesign in the other terminal type 
              > cp sky130_vsdinv.lef /home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a

![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/722778fc-c141-4d4d-b8f2-793d16a3f0eb)

        - Now if u check in the picorv terminal, the lef file will be copied 

![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/37de186e-57d2-4d89-a027-99fc34d1544e)

        - Modify the config.tcl by
             > vim config.tcl
        - In the design's config.tcl file add the below line to point to the lef location which is required during spice extraction.
               > set ::env(EXTRA_LEFS) [glob $::env(OPENLANE_ROOT)/designs/$::env(DESIGN_NAME)/src/*.lef]

![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/8ffe7b20-d457-4a99-84a9-0f5188025722)
       
        - Open the OpenLANE interactive window and retrieve the 0.9 package.
        - Include the below command to include the additional lef into the flow:
               > prep -design picorv32a -tag 16-09_10-10 -overwrite
               > set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
               > add_lefs -src $lefs
        - Run the interactive mode by the command
               > run_synthesis

![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/5d8e7528-e7f6-4e0f-a7d1-4f2cbfb0769a)


![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/055fc458-9baa-4a95-b337-e39f1ed09c07)

        - Once the synthesis is successfull we get the following output

![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/054c48a0-4b94-4502-bf8f-d348d233538f)


![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/aba411fd-4484-48d6-abe3-5afa1ba3dad8)


![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/4fefa4c4-77b6-4e45-b0d7-86d7bd3e830b)
  

           - To run the floorplans and placements we typr the following commands
                > run_floorplan
                > run_placement
                
  
![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/b805d7ea-354d-4e41-b761-e86cdf57dc20)


![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/8e3b333a-35f9-4830-9e18-fa25f2be744f)


             - magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.placement.def &


![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/cf2dec3c-046d-41ee-9e25-a89e53c5b1d7)


![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/d50f0c5e-3b2a-4069-aaad-f24e8a395687)




## TIMMING ANALYSIS WITH REAL CLOCKS USING OPEN STA

         - Configure OpenSTA for Post-Synth Timing Analysis
         - We must create two files
              - The first one must be in the openlane directory
              - This file is known as the 'pre_sta.conf' file.

![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/aeec25c6-c897-4218-be0b-62a048c76a54)

              - The second is the my_base.sdc file.
              - This should be in the 'src/sky130' directory under the picorv32a directory.
             
![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/d73a4a04-6bbf-4010-b7f2-8c3427dd0b12)

              - To run tyming analysis we type 
                    > sta pre_sta.conf

![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/ac22c1af-3022-4ad5-b5b8-e4427e1bc888)

             - There is a slack violation
             - Settinf MAX_FANOUT value to 4 reduces the slack violation.

![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/1a62d227-1a3c-4a71-880d-cf7dd8b45eb6)


## Clock Tree Synthesis TritonCTS and Signal Integrity
### Run CTS

             -  To run CTS we need to type the command
                       > run_cts
                       > New .v is created

![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/b1f93411-14b4-4f47-b523-4c1d7eb71913)

#### Timing Analysis with Real CLocks using OpenSTA

             - First we type the command 
                    > openroad.
             - Then we read the .lef file using the command
                    > read_lef /openLANE_flow/designs/picorv32a/runs/16-09_19-58/tmp/merged.lef

![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/f59877a7-4736-4229-94c6-305a1b1c0ad6)

              - Then we read the .def file.
                     > read_def /openLANE_flow/designs/picorv32a/runs/16-09_19-58/results/cts/picorv32a.cts.def

![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/4252f6d9-60ca-482c-b9a5-08c817848f84)

              - Then we type the below commands
                     > write_db pico_cts.db
                     > read_db pico_cts.db
                     > read_verilog /openLANE_flow/designs/picorv32a/runs/16-09_19-58/results/synthesis/picorv32a.synthesis_cts.v
                     > read_liberty -max $::env(LIB_SLOWEST)
                     > read_liberty -max $::env(LIB_FASTEST)

![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/9f159716-cc50-4088-904f-9fadb4184353)

              - We read the .src file
                    > read_sdc /openLANE_flow/designs/picorv32a/src/sky130/my_base.sdc

![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/22e69c85-7822-44ee-a544-fb9cad238a1d)

              - We set the clock and then check it
                    > set_propagated_clock [all_clocks]
                    > report_checks -path_delay min_max -format full_clock_expanded -digits 4

![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/b23d8d20-7df9-485c-af23-44a2f6fde7ff)


![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/a0ac65cd-eb98-4df7-8b0d-bd4127d033f8)


              - We perform it again for the more accurate result
              
![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/215dd64d-4a1a-4e68-bf06-a89273648a12)


![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/8e7259aa-ab61-4bb9-b2c0-fbbf47fbe6d2)


![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/5d16114e-0883-42d1-886b-b064d5426d76)

              -  Next type the following commands 
                   > report_clock_skew -hold
                   > report clock_skew -setup

![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/86212a96-c004-49c9-824b-3b69c66927f3)



[Back to COURSE](https://github.com/Vinodkumar8318/Pes_Openlane_work/tree/main#course)

</details>
<details>
<summary>DAY 5 : Final steps for RTL2GDS using triton route and openSTA </summary>
<br>

## Power Distribution Network and Routing

After generating our clock tree network and verifying post routing STA checks we are ready to generate the power distribution network gen_pdn in OpenLANE:

     The PDN feature within OpenLANE will create:

          Power ring global to the entire core
          Power halo local to any preplaced cells
          Power straps to bring power into the center of the chip
          Power rails for the standard cells

   ### Build Power Distribution network
   
![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/5d1ea9af-11c2-4200-8fb4-ac7850ffa1dd)


![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/1f2915be-f8fc-4fb4-a192-3e2c30afa917)


   ### Global and Detailed Routing

   - OpenLANE uses TritonRoute as the routing engine run_routing for physical implementations of designs. Routing consists of two stages:
           > Global Routing - Routing guides are generated for interconnects on our netlist defining what layers, and where on the chip each of the nets will be reputed
           > Detailed Routing - Metal traces are iteratively laid across the routing guides to physically implement the routing guides

   - If DRC errors persist after routing the user has two options:
           > Re-run routing with higher QoR settings
           > Manually fix DRC errors specific in tritonRoute.drc file

  ### SPEF Extraction

    - After routing has been completed interconnect parasitics can be extracted to perform sign-off post-route STA analysis. The parasitics are extracted into a SPEF file. The SPEF extractor 
      is not included within OpenLANE as of now.
           > cd ~/Desktop/work/tools/SPEFEXTRACTOR
           > python3 main.py <path to merged.lef in tmp> <path to def in routing>
    - The SPEF File will be generated in the location where def file is present


[Back to COURSE](https://github.com/Vinodkumar8318/Pes_Openlane_work/tree/main#course)
