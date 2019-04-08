# Cross App UX Initiative
What is described below is list of features that will enhance the user experience of the Aragon app ecosystem. After spending one year designing and developing Aragon apps, the Autark team has learned a lot.

Autark has a Cross App UX initiative that will make progress on many of these features, but it ultimately needs to be (and already is in ways) a Network-wide, cross-team and community initiative if we want to make *speedy* progress and also cater toward the immediate needs of the ecosystem.

# Let it be known: what features are missing from the list?

Feature requests should be app agnostic and *global*, as this initiative relates to the higher-level, *cross application UX*. Examples of feature requests that *SHOULD NOT* be included are ones that are as follows: 
* I want the Finance app to allow CSV exports
* I want a Task Management app

Feel free to create issues in this repo or discuss on the forum: https://forum.aragon.org/t/cross-application-ux-initiative-part-1/742

Note: thanks to all the Aragon app developers who participated in our survey -- that helped us identify some of the pain points.

# Curating feature requests
Once we have gathered feature requests, we can curate the features as an experiment, using the rinkeby deployment of the Planning Suite's Projects app -- which has a Github integration (coming this month). I'm not sure if this should be an Aragon Coop rinkeby DAO or something different. Coop and Non-coop members, what are your thoughts? The list of priorities won't be an immediate source of truth, but I think it can be a fun way to start to use the Planning Suite and to make progress on creating an ecosystem-wide priority list.

Aragon One team: if there is a related ticket already captured in one of your repos (whether described below, or something not on the list), please share. It would also be great to know what is on your roadmap related to the features described below.
____

*Note: The features below are not ranked in any particular order at the moment -- the numbers have been added for easy reference and refer to the issue numbers in the repo.*

## 1. Ability to manage global metadata, on a DAO by DAO basis, and share this metadata across a DAO's apps
* E.g conditionally link DAO-managed data blobs into a DAO’s apps: having a link to bylaws/manifesto/code of conduct in the Aragon Court, or the Projects app (when applying for work)
* E.g Managing your DAO's theme/branding/identity

## 2. Deep links to an App object (for the detail or panel view)
* E.g. so I can copy and paste what is in my browser bar and it points to a specific vote like mainnet.aragon.org/#/.../...?id=x

## 3. Ability to click on a link in `App A` that takes the user to `App B`
* E.g. click on a Finance app transaction in Finance app to see voting results in Voting app

## 4. Short and simple human-readable URLs
* e.g. Access a vote in your DAO via a link like mainnet.aragon.org/voting.autark.eth/obj?id=1
where `voting` is the instance of the voting app I have installed into my DAO [does it require ENS enhancement?]

## 5. Ability for radspec (or radspec-like tools) to reference params not in the function
* There are many use cases where one will want to provide the user additional context from the contract that may not be a param for the transaction they are signing.

## 6. Ability to forward metadata and/or a formatted data blob to an external (Voting) app
* Use cases:
  * Bulk Bounties: A list of issues &amp; bounty amounts forwarded from the Projects app to the Voting app for the DAO to approve.
  * Allocations: A list of possible options to distribute a budget towards, forwarded from the Allocations app to the Range Voting app.
* Related ticket: https://github.com/aragon/aragon/issues/452

## 7. Ability to dynamically render a feature in `App A` based on if `App B` is installed (yet not require both Apps to be installed by the user)
* e.g. If the Address Book is installed, render a dropdown menu in the Allocations app to select Address Book entries as options to send money to

## 8. Ability to render/utilize data from `App A` in `App B`
* e.g. Using the Address Book entries stored in the Allocations contract as the address data passed to the Range Vote contract
* Displaying the human readable names of Address Book entries in the Range Voting app [this will be solved with Identity Provider solution]

## 9. Ability to have complex multi-contract application systems
* The current sandboxing approach adds limitations to developing more complex applications. For example, it may be a more optimal experience to deploy `App A` which has one contract, and then enable `module B` within the app that provides additional functionality and whose logic is maintained in a separate contract (e.g. a user enables an Issue Curation module within the Projects app, or a Futarchy module within the Voting app).
* The current sandboxing approach leads towards an anti-pattern and doesn’t enable DRY application development across the ecosystem. For example, Pando may want to plug-in an Issue Curation module instead of up taking our entire Projects smart contract or rewriting that functionality within their contracts.
* Right now developers are working around this by building "a lot of "passthrough" functions into the main app contract in order to interact with multiple contracts.
* The optimal Voting UX is you have one "Voting" app in the left-panel, and within the app you have an initial "Dashboard" tab that displays all open votes (of all vote types), and then expanded views for each type that lists a comprehensive list. The information architecture may be as follows -- and knowing this information across all of your DAOs would even be better. 
![image|333x499](/images/daoing.png]

## 10. Ability to have “recipient” dropdowns that autocompletes human-readabale names that are mapped to ethereum addresses
* While progress has been made on identity providers (https://forum.aragon.org/t/identity-providers-resolving-addresses-to-identities-in-aragon/631), I do not see this initiative as complete until we can resolve how to resolve the identities in recipient dropdowns. I imagine this will require an additional component like `RecipientAutocomplete` instead of `DropDown` which has logic that interfaces with the Identity Provider API (it should work with all identity providers, and not just local labels)
* Related ticket: https://github.com/aragon/aragon-ui/issues/149

## 11. Ability to connect two or more external or internal actions that when done, can perform an intent in a DAO
* E.g. a person sends money to a contract and automatically gets minted a membership token to a DAO (supports subscription based DAOs). This is one example - many other use cases for triggers.
* Related topic: https://forum.aragon.org/t/aragon-triggers-enhanced-forwarding-interface-for-improved-composability/451

## 12. Ability to display pending actions which were forward from `App A` into `App B`, but have not yet been executed 
* Brett's words from related topic [https://forum.aragon.org/t/showing-pending-forwarded-actions-in-apps/709]: They go to an app, decide on an action, and sign a transaction (containing that action’s intent) that eventually gets mined. Afterwards they’re left in the dark, because they’ve received no feedback about what happened after and if they need to do anything (unless the intent was *synchronously* successful, e.g. the sender was the only possible voter in the entire organization). 
* There are many use cases for this: Finance app sending transfers, Token manager minting tokens, Allocations app proposing allocations, Permissions app upgrading permissions etc -- any app that is managed by a Voting-like app, essentially.

## 13. Improve the display and interfacing of multi-token DAOs
* DAOs will start to become complex and will have different "tokens" to manage different actions. This will require changes to the wrapper to be able to filter apps by token, or to allow a single app interface to work with multiple tokens.
* E.g. if a Finance app transfer is $50,000 or greater, send to ANT Voting app for approval, if Finance transfer is 0-$12,500 send to agp10 Voting app -- but you can see all of finance proposals within a single Voting app in your DAO.

## 14. Allow apps to create multi-step or multi-transaction signing interactions
* Brett's words: "some apps may require complex interactions with a user where multiple transactions or signatures must be signed in a row (e.g. token approvals come to mind). It would be nice if the apps had some way to declare this, and for clients to show these as step by step interactions rather than just multiple signing requests popping up."
* Related ticket: https://github.com/aragon/aragon/issues/609
___

### There are workarounds, implementation ideas, and work in progress for some of the features described above -- those will be described in subsequent forum posts this month.
