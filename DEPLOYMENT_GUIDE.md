# Install TijaPass V6 without disturbing V5

1. Download `TijaPass_V6_Intelligent_Accounting.zip` and **Extract All**.
2. GitHub → **+ → New repository** → name it `TijaPass-V6-Accounting` → Create.
3. Open the extracted inner `TijaPass_V6_Intelligent_Accounting` folder on your computer.
4. On GitHub: **Add file → Upload files**. Upload the **contents** of this folder, including `src`, `public`, `package.json`, `index.html`, `netlify.toml`. Commit changes.
5. Netlify → **Add new project → Import existing project → GitHub** → select the new repository.
6. Netlify build command: `npm run build`. Publish directory: `dist`. Deploy.
7. Under Netlify's project settings, rename the project (if available) to `tfltijapass6` (site: `https://tfltijapass6.netlify.app`). Do not rename/replace the old `tfltijapass` project.
8. Check **Deploys → Published**. If it fails, copy the first relevant red error from the deploy log; do not upload the ZIP into your existing application's `src` folder.
9. Open the V6 site → select **English / Kiswahili** in the header → **TFL Admin → Smart Accounting** → test the three methods. Use only fictional records.
10. To test the customer-import confirmation: change role to **Customer**, open **Smart Accounting → Review & verify**, provide payer and purpose, confirm; switch back to TFL Admin to approve.

**Supabase caution**: This ZIP does not connect live to Supabase just because environment variables exist. The schema is a developer implementation plan. Never publish sensitive credentials or real banking data in this browser demo.
