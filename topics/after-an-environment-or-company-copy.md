# After an environment or company copy

**Environment copy**

When an environment is copied in the Business Central admin center, **Digipoort Connector Setup** is set back to **Acceptation** and **Active** is turned off in every company of the new environment. This happens for every copy, whichever type of environment is copied to which. No action is needed and no message is shown. After the copy, VAT declarations in the new environment follow the standard route until an administrator turns **Active** on again.

When the new environment is a production environment (for example, a sandbox copied to production), an administrator opens **Digipoort Connector Setup**, selects **Production** again and turns on **Active** in each company that files officially.

A copy has more effects that an administrator must handle before you submit declarations from the new environment:

- Standard Business Central clears **Digipoort Delivery URL** and **Digipoort Status URL** on the **Elec. Tax Declaration Setup** page. Turning **Active** on again in **Digipoort Connector Setup** fills them for VAT declarations via Digipoort. For ICP declarations, which use the standard route, fill in the real Digipoort URLs again before you submit one or receive response messages.
- After a copy, **Allow HttpClient Requests** is off for every extension. In a sandbox, Digipoort Connector for Dutch VAT cannot call Semansys until it is turned on. *Test Connection* then shows the error described in [Connection to Semansys and call log](connection-to-semansys-and-call-log.md).
  1. Search for **Extension Management** and open it.
  2. Select the line **Digipoort Connector for Dutch VAT** and choose **View**. The **Extension Settings** page opens.
  3. Turn on **Allow HttpClient Requests**.

**Company copy**

When you copy a company with **Copy** on the **Companies** page, **Active** is turned off in **Digipoort Connector Setup** of the new company; its **Environment** is copied unchanged. Turn **Active** on in the new company only when it should submit VAT declarations via Digipoort, and check the **Environment** first. The company you copied from keeps its settings. No extra question or message is shown; you only see the standard message that the company was copied.

**Restoring an environment**

Digipoort Connector for Dutch VAT does **not** reset the setup when an environment is restored to a point in time. After a restore to a new environment, open **Digipoort Connector Setup** in every company and check the **Environment** field. Set it to **Acceptation** where the new environment must not file officially.
