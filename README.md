# Bss
document.addEventListener('DOMContentLoaded', () => {
    const activityInput = document.getElementById('activity');
    const addButton = document.getElementById('addButton');
    const activitiesList = document.getElementById('activities');
    const activityCount = document.getElementById('activityCount');

    let activities = [];

    function updateActivityCount() {
        activityCount.textContent = activities.length;
    }

    function renderActivities() {
        activitiesList.innerHTML = '';
        activities.forEach((activity, index) => {
            const li = document.createElement('li');
            li.textContent = activity;
            
            const deleteButton = document.createElement('button');
            deleteButton.textContent = 'Delete';
            deleteButton.addEventListener('click', () => {
                activities.splice(index, 1);
                renderActivities();
                updateActivityCount();
            });

            li.appendChild(deleteButton);
            activitiesList.appendChild(li);
        });
    }

    addButton.addEventListener('click', () => {
        const activity = activityInput.value.trim();
        if (activity) {
            activities.push(activity);
            activityInput.value = '';
            renderActivities();
            updateActivityCount();
        }
    });
});
