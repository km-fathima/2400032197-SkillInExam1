# 2400032197-SkillInExam1
Two developers are working on the same file App.js
# Step 1: Initialize repository
mkdir myproject
cd myproject
git init

# Step 2: Create initial App.js file
echo "function greet() {
    console.log('Hello, World!');
}

greet();" > App.js

git add App.js
git commit -m "Initial commit with greet function"

# Step 3: Create feature1 branch (Alice)
git checkout -b feature1

# Modify App.js for feature1
echo "function greet() {
    console.log('Hello from Alice!');
}

greet();" > App.js

git add App.js
git commit -m "Alice modifies greet function"

# Step 4: Create feature2 branch (Bob) from main
git checkout main
git checkout -b feature2

# Modify App.js for feature2
echo "function greet() {
    console.log('Hello from Bob!');
}

greet();" > App.js

git add App.js
git commit -m "Bob modifies greet function"

# Step 5: Merge feature1 into main
git checkout main
git merge feature1

# Step 6: Merge feature2 into main (conflict occurs)
git merge feature2 || echo "Conflict occurred! Resolve App.js manually."

# At this point, App.js will look like this:
# <<<<<<< HEAD
# console.log('Hello from Alice!');
# =======
# console.log('Hello from Bob!');
# >>>>>>> feature2

# Step 7: Manually edit App.js to resolve conflict
echo "function greet() {
    console.log('Hello from Alice and Bob!');
}

greet();" > App.js

git add App.js
git commit -m "Resolved merge conflict between feature1 and feature2"

# Step 8: Verify
git log --oneline --graph --all
git status
