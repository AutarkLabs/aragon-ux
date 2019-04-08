# aragon-ux
Feature requests to enhance Aragon's UX


## 1. Ability to manage global metadata, on a DAO by DAO basis, and share this metadata across a DAO's apps
* E.g conditionally link DAO-managed data blobs into a DAO’s apps: having a link to bylaws/manifesto/code of conduct in the Aragon Court, or the Projects app (when applying for work)
* E.g Managing your DAO's theme/branding/identity

## 2. Ability to navigate to a deep link of an App object (for the detail or panel view) and ability to have human-readable identifiers for app names in the URLs
* e.g. Access a vote in your DAO via a link like mainnet.aragon.org/autark.eth/voting?id=1
where `voting` is the instance of the voting app I have installed into my DAO

## 3. Ability for radspec (or radspec-like tools) to reference params not in the function
* There are many use cases where one will want to provide the user additional context from the contract that may not be a param for the transaction they are signing.

## 4. Ability to forward metadata and/or a formatted data blob to an external (Voting) app
* Use cases:
  * Bulk Bounties: A list of issues &amp; bounty amounts forwarded from the Projects app to the Voting app for the DAO to approve.
  * Allocations: A list of possible options to distribute a budget towards, forwarded from the Allocations app to the Range Voting app.
* Related ticket: https://github.com/aragon/aragon/issues/452

## 5. Ability to dynamically render a feature in `App A` based on if `App B` is installed (yet not require both Apps to be installed by the user)
* e.g. If the Address Book is installed, render a dropdown menu in the Allocations app for to select Address Book entries as options to send money to

## 6. Ability to render/utilize data from `App A` in `App B`
* e.g. Using the Address Book entries stored in the Allocations contract as the address data passed to the Range Vote contract
* Displaying the human readable names of Address Book entries in the Range Voting app [this will be solved with Identity Provider solution]

## 7. Ability to have complex multi-contract application systems
* This can add limitations to develop more complex applications. For example, it may be a more optimal experience to deploy `App A` which has one contract, and then enable `module B` within the app that provides additional functionality and whose logic is maintained in a separate contract (e.g. a user enable the Issue Curation module within the Projects app). 
* The current sandboxing approach leads towards an anti-pattern and doesn’t enable DRY application development across the ecosystem. For example, Pando may want to plug-in an Issue Curation module instead of up taking our entire Projects smart contract or rewriting that functionality within their contracts.
* The optimal Voting UX is you have one "Voting" app in the left-panel, and within the app you have an initial "Dashboard" tab that displays all open votes (of all vote types), and then expanded views for each type that lists a comprehensive list. The information architecture may be as follows -- and knowing this information across all of your DAOs would even be better. 
![daoing](/images/daoing.png) 

## 8. Ability to have “recipient” dropdowns that autocomplete a human-readbale name.
* While progress has been made on identity providers (https://forum.aragon.org/t/identity-providers-resolving-addresses-to-identities-in-aragon/631), I do not see this initiative as complete until we can resolve how to resolve the the identities in recipient dropdowns. I imagine this will require an additional component like `RecipientAutocomplete` instead of `DropDown` which has logic that interfaces with the Identity Provider API.

## 9. Ability to connect two or more external or internal actions that when done, can perform an intent in a DAO.
* E.g. a person sends money to a contract and automatically gets minted a membership token to a DAO (supports subscription based DAOs). This is one example - many other use cases for triggers.
* Related topic: https://forum.aragon.org/t/aragon-triggers-enhanced-forwarding-interface-for-improved-composability/451

## 10. Ability to display pending actions which were forward from `App A` into `App B`, but have not yet been executed. 
* Brett's words from related topic [https://forum.aragon.org/t/showing-pending-forwarded-actions-in-apps/709]: They go to an app, decide on an action, and sign a transaction (containing that action’s intent) that eventually gets mined. Afterwards they’re left in the dark, because they’ve received no feedback about what happened after and if they need to do anything (unless the intent was *synchronously* successful, e.g. the sender was the only possible voter in the entire organization). 
* There are many use cases for this: Finance app sending transfers, Token manager minting tokens, Allocations app proposing allocations, Permissions app upgrading permissions etc -- any app that is managed by a Voting-like app, essentially.

## 11. Improve the display and interfacing of multi-token DAOs
* DAOs will start to become complex and will have different "tokens" to manage different actions. This will require changes to the wrapper to be able to filter apps by token, or to allow a single app interface to work with multiple tokens.
* E.g. if a Finance app transfer is $50,000 or greater, send to ANT Voting app for approval, if Finance transfer is 0-$12,500 send to agp10 Voting app -- but you can see all of finance proposals within a single Voting app in your DAO.
