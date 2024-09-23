# youtube_not_interested



// Function to wait for a given amount of time
function wait(ms) {
    return new Promise(resolve => setTimeout(resolve, ms));
}

(async function() {
    // Select all "Action menu" buttons with the specified class and aria-label
    let actionMenuButtons = document.querySelectorAll('.style-scope.yt-icon-button[aria-label="Action menu"]');

    // Use a for loop to handle async behavior (waiting for each action)
    for (let key = 0; key < actionMenuButtons.length; key++) {
        let element = actionMenuButtons[key];

        // Simulate a click on the action menu button
        element.click();
        console.log(`Clicked Action Menu Button ${key + 1}`);

        // Wait for the menu to load (1 second delay, adjust as necessary)
        await wait(1000);

        // Find all "Not interested" elements
        let notInterestedElements = document.querySelectorAll('yt-formatted-string.style-scope.ytd-menu-service-item-renderer');

        // Check if the 5th element (index 4) contains the text "Not interested"
        if (notInterestedElements[4] && notInterestedElements[4].textContent.trim() === "Not interested") {
            console.log(`Found 'Not interested' element for Button ${key + 1}:`, notInterestedElements[4]);

            // Simulate a click on the 'Not interested' element
            notInterestedElements[4].click();
            console.log(`Clicked 'Not interested' for Button ${key + 1}`);
        } else {
            console.log(`'Not interested' element not found or text doesn't match for Button ${key + 1}.`);
        }

        // Wait a bit before moving on to the next button
        await wait(1000); // Adjust the wait time if necessary
    }
})();
