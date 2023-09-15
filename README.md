# OPENLANE 

## ABOUT THE REPOSITORY
OpenLane is an automated RTL to GDSII flow based on several components including OpenROAD, Yosys, Magic, Netgen, CVC, SPEF-Extractor, KLayout and a number of custom scripts for design exploration and optimization. The flow performs all ASIC implementation steps from RTL all the way down to GDSII.

You can check out the documentation, including in-depth guides and reference manuals at [ReadTheDocs](https://openlane.readthedocs.io/).


 # COURSE 
<details>
<summary>DAY 1 : Insecption of open-source EDA, Openlane and sky130pdk </summary>
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

![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/dfddb70d-2147-4b62-b61d-64f7da861b80)


![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/3d20283b-3f96-4354-a13f-21dc8cc03b3f)

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
 
 ![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/955048e2-542b-4c18-8d0f-b976fad8e0cc)
 

 ![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/e11daa35-37e2-43e5-ab56-fccd9cad5ee0)





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

        - 










[Back to COURSE](https://github.com/Vinodkumar8318/Pes_Openlane_work/tree/main#course)

</details>
<details>
<summary>DAY 3: Design library cell using magic layout and ngspice characterization </summary>
<br>

[Back to COURSE](https://github.com/Vinodkumar8318/Pes_Openlane_work/tree/main#course)

</details>
<details>
<summary>DAY 4 : Prelayout timming layout analysis and inportance of good clock tree </summary>
<br>

[Back to COURSE](https://github.com/Vinodkumar8318/Pes_Openlane_work/tree/main#course)

</details>
<details>
<summary>DAY 5 : Final steps for RTL2GDS using triton route and openSTA </summary>
<br>

[Back to COURSE](https://github.com/Vinodkumar8318/Pes_Openlane_work/tree/main#course)
