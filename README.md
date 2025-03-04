<!DOCTYPE html>
<html lang="en">
<body>

  <h1>Atithidev Serverless API 🌐</h1>

  <h2>Overview 📝</h2>
  <p>This is a <strong>Serverless AWS Lambda Function-based API</strong> for the <strong>Atithidev Website</strong>. It provides endpoints to manage hosts and reviews using <strong>MongoDB Atlas</strong> as the database. The API is deployed using the <strong>Serverless Framework</strong> with <strong>CI/CD automation</strong>.</p>

  <h2>Features ✨</h2>
  <ul>
    <li><strong>Fetch hosts and reviews</strong> 🗂️</li>
    <li><strong>Insert new reviews</strong> 📝</li>
    <li><strong>Fully serverless with AWS Lambda</strong> ⚡</li>
    <li><strong>Uses MongoDB Atlas as the database</strong> 🗄️</li>
    <li><strong>CI/CD automation with GitHub Actions</strong> 🤖</li>
    <li><strong>ESLint integration for code quality enforcement</strong> ✅</li>
    <li><strong>✅ Automated cleanup with Serverless Prune Plugin 🧹</li>
  </ul>

  <h2>CI/CD Integration 🤖</h2>
  <p>The project uses <strong>GitHub Actions</strong> for automated CI/CD pipelines, ensuring smooth and reliable deployments. Here's how it works:</p>

  <h3>CI/CD Workflow 🔄</h3>
  <ol>
    <li><strong>Trigger:</strong> 🚀 Pushing to the <code>main</code> branch triggers the CI/CD pipeline.</li>
    <li><strong>Linting:</strong> ✅ ESLint runs to check code quality. If errors are found, the pipeline stops, and deployment is blocked.</li>
    <li><strong>Dependency Installation:</strong> 📦 Only production dependencies (<code>--production</code> flag) are installed to optimize the deployment package.</li>
    <li><strong>Deployment:</strong> 🚀 The <strong>Serverless Framework</strong> deploys the application to <strong>AWS Lambda</strong> if all checks pass.</li>
    <li><strong>Secure Credentials:</strong> 🔐 AWS credentials (<code>AWS_ACCESS_KEY_ID</code> and <code>AWS_SECRET_ACCESS_KEY</code>) are securely managed using <strong>GitHub Secrets</strong>.</li>
  </ol>

  <h4>Benefits of CI/CD Automation:</h4>
  <ul>
    <li><strong>Faster Deployments:</strong> 🚀 Automated pipelines reduce manual effort and speed up deployments.</li>
    <li><strong>Consistent Quality:</strong> ✅ ESLint ensures code quality is maintained across all deployments.</li>
    <li><strong>Secure Practices:</strong> 🔐 Sensitive credentials are never exposed in the codebase.</li>
  </ul>

  <h2>Security Features 🔒</h2>
  <ul>
    <li><strong>AWS Secrets Management:</strong> 🔐 <code>AWS_ACCESS_KEY_ID</code> and <code>AWS_SECRET_ACCESS_KEY</code> are securely stored in <strong>GitHub Secrets</strong> to prevent exposure in the codebase.</li>
    <li><strong>Environment Variables Protection:</strong> 🚫 The <code>.env</code> file is added to <code>.gitignore</code> to ensure sensitive information like <code>MONGO_URI</code> is not accidentally committed to the repository.</li>
    <li><strong>Code Quality Enforcement:</strong> ✅ <strong>ESLint</strong> is integrated into the CI/CD pipeline to enforce coding standards and prevent low-quality or insecure code from being deployed.</li>
    <li><strong>Least Privilege Principle:</strong> 🔑 AWS IAM roles are configured with minimal permissions required for the Lambda functions to interact with MongoDB Atlas and other AWS services.</li>
    <li><strong>Database Security:</strong> 🗄️ MongoDB Atlas is configured with IP whitelisting, encryption at rest, and network isolation to ensure data security.</li>
  </ul>

  <h2>Tech Stack 🛠️</h2>
  <ul>
    <li><strong>Node.js</strong> (Runtime: 18.x) 🟢</li>
    <li><strong>Express.js</strong> (Lightweight API Framework) 🚀</li>
    <li><strong>MongoDB Atlas</strong> (Database) 🍃</li>
    <li><strong>AWS Lambda</strong> (Serverless Functions) ⚡</li>
    <li><strong>Serverless Framework</strong> (Deployment & CI/CD) 🛠️</li>
    <li><strong>GitHub Actions</strong> (CI/CD Pipeline) 🤖</li>
    <li><strong>ESLint</strong> (Code Quality) ✅</li>
  </ul>

  <h2>Setup Instructions 🛠️</h2>

  <h3>1. Clone the Repository 📥</h3>
  <pre><code>git clone https://github.com/ap-dev-github/atithidev-mongoose-api.git
cd atithidev-mongoose-api</code></pre>

  <h3>2. Install Dependencies 📦</h3>
  <pre><code>npm install</code></pre>

  <h3>3. Environment Variables 🔐</h3>
  <p>Create a <code>.env</code> file in the root directory and add your MongoDB connection string:</p>
  <pre><code>MONGO_URI=your-mongodb-connection-string</code></pre>
  <p><strong>Note:</strong> Make sure <code>.env</code> is added to <code>.gitignore</code> to prevent exposing secrets.</p>

  <h3>4. Run Locally with Serverless Offline 🖥️</h3>
  <pre><code>npx serverless offline</code></pre>
  <p>This will start the API locally.</p>

  <h3>5. Deploy to AWS Lambda 🚀</h3>
  <pre><code>npx serverless deploy</code></pre>
  <p>This will deploy the API to AWS.</p>

  <h2>Endpoints 🌐</h2>
  <table>
    <thead>
      <tr>
        <th>Method</th>
        <th>Endpoint</th>
        <th>Description</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td><code>GET</code></td>
        <td><code>/</code></td>
        <td>Home route, checks if API is running</td>
      </tr>
      <tr>
        <td><code>GET</code></td>
        <td><code>/fetchHosts</code></td>
        <td>Fetch all hosts</td>
      </tr>
      <tr>
        <td><code>GET</code></td>
        <td><code>/fetchHosts/:state</code></td>
        <td>Fetch hosts by state</td>
      </tr>
      <tr>
        <td><code>GET</code></td>
        <td><code>/fetchHost/:id</code></td>
        <td>Fetch a host by ID</td>
      </tr>
      <tr>
        <td><code>GET</code></td>
        <td><code>/fetchReviews/host/:id</code></td>
        <td>Fetch reviews for a specific host</td>
      </tr>
      <tr>
        <td><code>POST</code></td>
        <td><code>/insert_review</code></td>
        <td>Insert a new review</td>
      </tr>
    </tbody>
  </table>

  <h2>Important Notes 📌</h2>
  <ul>
    <li><strong>AWS Credentials:</strong> Set up <code>AWS_ACCESS_KEY_ID</code> and <code>AWS_SECRET_ACCESS_KEY</code> as <strong>GitHub Secrets</strong> for CI/CD deployment.</li>
    <li><strong>MongoDB Connection:</strong> Ensure the <code>MONGO_URI</code> is correctly set in your <code>.env</code> file or <strong>AWS Lambda environment variables</strong>.</li>
    <li><strong>Serverless Framework:</strong> Install globally if not installed:
      <pre><code>npm install -g serverless</code></pre>
    </li>
    <li><strong>Linting:</strong> The project uses <strong>ESLint</strong> for code quality. Run:
      <pre><code>npx eslint .</code></pre>
      before deployment to check for issues.
    </li>
  </ul>

  <h2>License 📄</h2>
  <p>This project is licensed under the <strong>MIT License</strong> - see the <a href="LICENSE">LICENSE</a> file for details.</p>

  <h2>Created & Maintained By 👨‍💻</h2>
  <p><strong>Ayush Pandey</strong> | Contact: <a href="mailto:ayushpandey.cs@gmail.com">ayushpandey.cs@gmail.com</a> 📧</p>
  <p>LinkedIn: <a href="https://www.linkedin.com/in/linkedap/">Ayush Pandey</a> 🔗</p>

</body>
</html>
