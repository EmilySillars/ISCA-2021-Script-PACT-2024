# Adapting Scripts for PACT PC Meeting

## Setup (from README.md)

0. ```
   cd ISCA-2021-Script-PACT-2024
   ```

1. ```
   conda create -n COI_Redistributable python=3.6.12
   conda activate COI_Redistributable
   ```

2. ```
   pip install -r requirements.txt
   ```

When you are done working, exit environment with ```conda deactivate      ```

## What do we need to get from HotCRP to run the scripts?

1. We need the CSV file downloaded via the **Getting DBLP Person ID** instructions:

   The input to this script is a CSV file contains the PC info from HotCRP. To obtain this CSV file, go to the `Users` on the side-panel of your HotCRP conference page which will bring you to the list of users registered. In the `User Selection` on the top, select `Program committee` and click `Go` which will display all PC members. Then, go to the bottom of the page, click `select all xxx, then Download:` and choose `PC info`. Click `Go` to download the CSV file.

   The header of this CSV file is shown below.

   ```
   first,last,email,affiliation,country,roles,tags,collaborators,follow,"topic: ...","topic: ...",...
   ```

2. The CSV file that contains the list of papers with their selected topics.

   This file is obtained from HotCRP by clicking `Search` on the Search Field `All` in `Submitted`. Then, move to the bottom of the page, click `select all xxx` and click `Download`. Select `Topics` on `Paper Information` submenu, then click `Go`.

   The header of this CSV file is shown below.

   ```
   paper,title,topic
   ```

3. The CSV file that contains the list papers alongside of their authors. ***(used by both Paper Discussion and Zoom Meeting Config)***

   This file is obtained from HotCRP by clicking `Search` on the Search Field `All` in `Submitted`. Then, move to the bottom of the page, click `select all xxx` and click `Download`. Select `Authors` on `Paper Information` submenu, then click `Go`.

   The header of this CSV file is shown below.

   ```
   paper,title,first,last,email,affiliation,country,iscontact
   ```

4. The CSV file that contains the list papers alongside with its data.  ***(used by both Paper Discussion and Zoom Meeting Config)***

   This file is obtained from HotCRP by clicking `Search` on the Search Field `All` in `Submitted`. Then, move to the bottom of the page, click `select all xxx` and click `Download`. Select `CSV` on `Paper Information` submenu, then click `Go`.

   The header of this CSV file is shown below.

   ```
   ID,Title,Authors,"# Reviews",Status,OveMer,Tags
   ```

5. COMMENT: WE ALREADY HAVE THIS SPREADSHEET.
   The CSV file that contains the list papers alongside with its PC conflict. ***(used by both Paper Discussion and Zoom Meeting Config)***

   This file is obtained from HotCRP by clicking `Search` on the Search Field `All` in `Submitted`. Then, move to the bottom of the page, click `select all xxx` and click `Download`. Select `PC Conflict` on `Paper Information` submenu, then click `Go`.

   The header of this CSV file is shown below.

   ```
   paper,title,first,last,email,conflicttype
   ```

6. The CSV file that contains the list papers alongside with its PC Reviewer Assignment.

   This file is obtained from HotCRP by clicking `Search` on the Search Field `All` in `Submitted`. Then, move to the bottom of the page, click `select all xxx` and click `Download`. Select `PC assignments` on `Review assignments` submenu, then click `Go`.

   The header of this CSV file is shown below.

   ```
   paper,action,email,round,title
   ```

7. The CSV file that contains the list papers alongside of their authors. (same as step 4)

8. The CSV file that contains the list papers alongside with its data. (same as step 5)

9. The CSV file that contains the list papers alongside with its PC conflict. (same as step 6)

## What do we need to create manually to run the scripts?

1. The CSV file that contains predefined topic priority.

   This file is created manually. It contains all of the  topics used in the conference and its numerical priority. The lower the  number, the higher the priority is. See the `sample-data/input/isca2021-topics-priority.csv` for more information. Note that the topic must be match with the topic defined in HotCRP.

2. The CSV file that contains the PC availability for each time slots.

   This file is created manually from Doodle by exporting the doodle data to Microsoft Excel. The numbered columns are the time slot  defined in the Doodle.
   *We collect the availability of PC member to attend the PC meeting using  Doodle. We have two discussion days which divided into 1-hour slot to  let each PC member choose which time slots they are available.  Alternatively, you can also use Google Form to collect this data. **Don't  forget to collect the email used in HotCRP to make us easier to  post-process the data.***

   **^ how will this scheduling differ for PACT?**

3. The CSV file that contains the PC members zoom email.

   This file is created manually from Google Form to collect the email address used to login into Zoom Client for each PC member.

   The header of this CSV file is shown below.

   ```
   Name,Institution,email,hotcrp_email,Zoom email 1,Zoom email 2
   ```

   *You will need to collect email used by each PC member to login into the  zoom account since the pre-assigned configuration will identify each  participant based on this email. We use Google Form to collect one  primary zoom email and one secondary zoom email (optional) alongside the full name and email address used in HotCRP.* 

## Troubleshooting

1. While running `pip install -r requirements.txt`, I encountered the following error:
   ```
   ERROR: Could not find a version that satisfies the requirement zeromq==4.3.4 (from versions: none)
   ERROR: No matching distribution found for zeromq==4.3.4
   ```

   Solution:

   ```
   conda install zeromq==4.3.4
   ```

   