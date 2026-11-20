# Set up with the assisted setup

## What this feature does

The assisted setup **Set up Digipoort Connector for Dutch VAT** guides an administrator through the setup of Digipoort Connector in a company, in one flow: the Digipoort environment, a connection test, the job queue entry that gets the Digipoort status, and turning the extension on. It is the quickest way to set up a company. You can still set everything up on the separate pages described in [Digipoort Connector Setup](digipoort-connector-setup.md), [Connection to Semansys and call log](connection-to-semansys-and-call-log.md) and [Submit VAT declarations via Digipoort](submit-vat-declarations-via-digipoort.md).

The assisted setup is listed on the **Assisted Setup** page in the group **Digipoort Connector for Dutch VAT**. The **Digipoort Connector Setup** page is also listed on the **Manual Setup** page, in the category **Digipoort Connector for Dutch VAT**.

The assisted setup is completed per company: completing it in one company does not complete it in another.

In Dutch, the assisted setup is called **Digipoort Connector for Dutch VAT instellen**, and the item that activates the license **Digipoort Connector activeren**.

## Setup

You need the **Digipoort Connector** permission set, or SUPER. In addition:
- To let the assisted setup create the job queue entry, you need permission to schedule background tasks (job queue entries). Without it, **Finish** shows *You are not allowed to schedule background tasks. Ask your system administrator to give you permission to do so. …* and nothing is changed; turn off **Create status job** to finish without it.
- To have the assisted setup marked as completed, you need permission to change assisted setups. Without it, everything else is done, but the assisted setup is not marked as completed and no message is shown.

The extension must be activated in Product Licensing. As long as it is not, **Assisted Setup** shows **Activate Digipoort Connector** instead of the assisted setup. Choose it to open **Bluace Products** for Digipoort Connector for Dutch VAT, and activate the extension there (see [Digipoort Connector Setup](digipoort-connector-setup.md)). The next time you open **Assisted Setup**, **Set up Digipoort Connector for Dutch VAT** is listed instead.

## How to use

**Set up a company**

1. Search for **Assisted Setup** and open it. In the group **Digipoort Connector for Dutch VAT**, choose **Set up Digipoort Connector for Dutch VAT**. The assisted setup opens with the title **Set up Digipoort Connector**; you can also search for that name.
   - When the license is not valid or not activated, the assisted setup does not open and an error is shown: *Digipoort Connector for Dutch VAT license is not valid or not activated.*
2. The first page explains what the extension does and the difference between **Acceptation** and **Production**. Choose **Next**.
3. In **Environment**, choose **Acceptation** or **Production**. The same rules apply as on **Digipoort Connector Setup**: in a sandbox, **Production** is refused, and otherwise you are asked to confirm **Production**. The environment is saved as soon as you change it.
   - When Digipoort Connector is already active in the company, **Environment** cannot be changed here. To change it, turn off **Active** on **Digipoort Connector Setup** first.
4. Choose **Next**. Choose **Test Connection** to sign in to Semansys for the environment you chose. The result and the possible errors are the same as for *Test the connection to Semansys* in [Connection to Semansys and call log](connection-to-semansys-and-call-log.md). You can continue when the test fails, for example when **Allow HttpClient Requests** still has to be turned on.
5. Choose **Next**. The page **Get the Digipoort status automatically** opens.
   - Leave **Create status job** turned on to create a job queue entry that gets the Digipoort status of submitted declarations once a day. Turn it off when you set up the job queue entry yourself, or do not want one. See *Get the Digipoort status automatically* in [Submit VAT declarations via Digipoort](submit-vat-declarations-via-digipoort.md).
   - When a job queue entry for **Get Digipoort Status** already exists, **Create status job** is turned off and cannot be changed, and the **Status** of the existing entry is shown. The assisted setup does not change that entry: when its **Status** is **On Hold** or **Error**, open **Job Queue Entries** and choose **Set Status to Ready** yourself.
6. Choose **Next**. The page **That's it!** opens. Leave **Turn on Active** turned on to switch VAT declarations in the company to Digipoort Connector. When Digipoort Connector is already active, this field is not shown and it stays active.
7. Choose **Finish**. Then:
   - When **Turn on Active** is turned on, **Active** is turned on, which fills empty Digipoort URLs on **Elec. Tax Declaration Setup**. When you turned it off, **Active** stays off.
   - When **Create status job** is turned on, the job queue entry is created and normally gets the **Status** **Ready**. It runs as you, for the first time right after **Finish** and then once a day.
   - The assisted setup is marked as completed for the company, also when you turned off **Turn on Active**.

After the assisted setup, check the setup of standard Business Central that VAT declarations need, such as **Elec. Tax Declaration Setup** and **Company Information**; the assisted setup does not check it. See *Setup* in [Submit VAT declarations via Digipoort](submit-vat-declarations-via-digipoort.md).

**Close the assisted setup before Finish**

When you close the assisted setup before you choose **Finish**, you are asked *Digipoort Connector has not been set up. Do you want to close the guide?* Choose **No** to continue. Choose **Yes** to close it: **Active** is not changed, no job queue entry is created and the assisted setup is not completed. The **Environment** you chose is kept, and a connection test you did stays in **Digipoort Log Entries**.

Good to know:
- You can run a completed assisted setup again from **Assisted Setup**. It shows the current settings of the company, and closing it asks nothing.
- The job queue entry runs as the user who chose **Finish**. That user needs the permissions to get the Digipoort status, see [Submit VAT declarations via Digipoort](submit-vat-declarations-via-digipoort.md).
- The job queue entry tries a failed run again within seconds, up to 3 times. Only when all tries fail does it stop with **Status** **Error**. See *Get the Digipoort status automatically* in [Submit VAT declarations via Digipoort](submit-vat-declarations-via-digipoort.md).
- The assisted setup never turns **Active** off and never changes an existing job queue entry.
