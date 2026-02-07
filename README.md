${sub.title || 'РџРѕРґР·Р°РґР°С‡Р°'}
вњЋ  рџ—‘
${sub.deadline || 'Р‘РµР· СЃСЂРѕРєР°'}
${sub.completed ? 'Р’С‹РїРѕР»РЅРµРЅРѕ' : 'Р’ РїСЂРѕС†РµСЃСЃРµ'}
Р”РµР№СЃС‚РІРёСЏ:
${(sub.actions || []).map((act, aidx) => `
${act.title}
рџ—‘
`).join('')}  
РЎРїСѓСЃРєРѕРІРѕР№ РєСЂСЋС‡РѕРє (РЅР°С‡Р°Р»СЊРЅС‹Р№ С€Р°Рі):

Р—Р°РјРµС‚РєРё:

`).join('')} `).join('')}
РЎС‚Р°С‚РёСЃС‚РёРєР°
${data.goals.length}
Р’СЃРµРіРѕ С†РµР»РµР№
${data.goals.filter(g => g.completed).length}
Р’С‹РїРѕР»РЅРµРЅРѕ
${Math.round(calculateProgress(type))}%
РџСЂРѕРіСЂРµСЃСЃ
${countOverdue(type)}
РџСЂРѕСЃСЂРѕС‡РµРЅРѕ
`; } function renderHealthPage() { const container = document.getElementById('health-content'); const data = appData.health; container.innerHTML = ` ${renderStandardPage('health')}
РњРѕРЅРёС‚РѕСЂРёРЅРі Р·РґРѕСЂРѕРІСЊСЏ
${data.stats.steps}
РЁР°РіРѕРІ СЃРµРіРѕРґРЅСЏ
${data.stats.calories}
РљР°Р»РѕСЂРёР№
${data.stats.sleep}С‡
РЎРѕРЅ
${data.stats.water}
РЎС‚Р°РєР°РЅРѕРІ РІРѕРґС‹
+1000 С€Р°РіРѕРІ  +100 РєРєР°Р»  +1 С‡Р°СЃ СЃРЅР°  +1 СЃС‚Р°РєР°РЅ
РљР°Р»СЊРєСѓР»СЏС‚РѕСЂ РєР°Р»РѕСЂРёР№
Р’РµСЃ (РєРі)  
Р РѕСЃС‚ (СЃРј)  
Р’РѕР·СЂР°СЃС‚  
РђРєС‚РёРІРЅРѕСЃС‚СЊ  
Р Р°СЃСЃС‡РёС‚Р°С‚СЊ РЅРѕСЂРјСѓ
РЁР°РіРѕРјРµСЂ Рё РјР°СЂС€СЂСѓС‚С‹
Р¦РµР»СЊ С€Р°РіРѕРІ РЅР° РґРµРЅСЊ  
РџР»Р°РЅРёСЂСѓРµРјС‹Р№ РјР°СЂС€СЂСѓС‚     Р”РѕР±Р°РІРёС‚СЊ РјР°СЂС€СЂСѓС‚
`; renderRoutes(); } function renderProductPage() { const container = document.getElementById('product-content'); const data = appData.product; container.innerHTML = `
10 РІРѕРїСЂРѕСЃРѕРІ РєРѕРЅС†РµРїС‚Р° РїСЂРѕРґСѓРєС‚Р°
${productQuestions.map((q, idx) => `
Р’РѕРїСЂРѕСЃ ${idx + 1}
${q}

`).join('')}
Р”РµР№СЃС‚РІРёСЏ РїРѕ РїСЂРѕРґСѓРєС‚Сѓ
+
${data.actions.map((act, idx) => `
${act.title}
рџ—‘
${act.deadline || 'Р‘РµР· СЃСЂРѕРєР°'} ${act.completed ? 'Р’С‹РїРѕР»РЅРµРЅРѕ' : 'Р’ РїСЂРѕС†РµСЃСЃРµ'}
`).join('')}
Р—Р°РјРµС‚РєРё РїРѕ РїСЂРѕРґСѓРєС‚Сѓ

`; } function renderFinancePage() { const container = document.getElementById('finance-content'); const data = appData.finance; const months = ['РЇРЅРІР°СЂСЊ', 'Р¤РµРІСЂР°Р»СЊ', 'РњР°СЂС‚', 'РђРїСЂРµР»СЊ', 'РњР°Р№', 'РСЋРЅСЊ', 'РСЋР»СЊ', 'РђРІРіСѓСЃС‚', 'РЎРµРЅС‚СЏР±СЂСЊ', 'РћРєС‚СЏР±СЂСЊ', 'РќРѕСЏР±СЂСЊ', 'Р”РµРєР°Р±СЂСЊ']; container.innerHTML = `
Р¤РёРЅР°РЅСЃРѕРІС‹Р№ РїР»Р°РЅ РЅР° РіРѕРґ
${months.map((m, idx) => ` ${m}
`).join('')}
Р”РѕС…РѕРґС‹
Р—Р°СЂРїР»Р°С‚Р°  
Р¤СЂРёР»Р°РЅСЃ  
РРЅРІРµСЃС‚РёС†РёРё/РџСЂРѕС†РµРЅС‚С‹  
${data.income.other.map((inc, idx) => `
Р”РѕРї. РґРѕС…РѕРґ ${idx + 1}
рџ—‘
`).join('')}
+ Р”РѕР±Р°РІРёС‚СЊ РєР°С‚РµРіРѕСЂРёСЋ
РС‚РѕРіРѕ РґРѕС…РѕРґРѕРІ:
${calculateTotalIncome()} в‚Ѕ
Р Р°СЃС…РѕРґС‹ (РјРёРЅ/РјР°РєСЃ)
${Object.entries(data.expenses).map(([key, val]) => `
${TranslateExpense(Key)}
 -  
`).join('')}
РС‚РѕРіРѕ СЂР°СЃС…РѕРґРѕРІ:
${calculateTotalExpense()} в‚Ѕ
РќР°РєРѕРїР»РµРЅРёСЏ Рё РґРѕР»РіРё
РќР°РєРѕРїР»РµРЅРёСЏ  
Р”РѕР»РіРё  
Р‘Р°Р»Р°РЅСЃ:
${calculateBalance()} в‚Ѕ
Р РµРєРѕРјРµРЅРґР°С†РёСЏ:
${getFinanceAdvice()}
РЎС‚Р°С‚РёСЃС‚РёРєР° Рё РіСЂР°С„РёРє
`; drawFinanceChart(); } // Helper Functions function getSuitColor(type) { const colors = { career: '#ff2a2a', capital: '#e0e0e0', experience: '#0080ff', personal: '#4a4a4a', purchases: '#8b4513', health: '#00ff88', business: '#ff8800', product: '#ff00ff', finance: '#ffbf00' }; return colors[type] || '#00d4ff'; } function getStatusClass(goal) { if (goal.completed) return 'status-active'; if (goal.deadline && new Date(goal.deadline) < new Date() && !goal.completed) return 'status-danger'; return 'status-warning'; } function getStatusText(goal) { if (goal.completed) return 'Р’С‹РїРѕР»РЅРµРЅРѕ'; if (goal.deadline && new Date(goal.deadline) < new Date()) return 'РџСЂРѕСЃСЂРѕС‡РµРЅРѕ'; return 'Р’ РїСЂРѕС†РµСЃСЃРµ'; } function calculateProgress(type) { const data = appData[type]; if (!data.goals || data.goals.length === 0) return 0; let total = 0; let completed = 0; data.goals.forEach(goal => { total++; if (goal.completed) completed++; if (goal.subtasks) { goal.subtasks.forEach(sub => { total++; if (sub.completed) completed++; }); } }); return total > 0 ? (completed / total) * 100 : 0; } function countOverdue(type) { const data = appData[type]; if (!data.goals) return 0; return data.goals.filter(g => { if (g.completed) return false; if (g.deadline && new Date(g.deadline) < new Date()) return true; return false; }).length; } function updateProgress() { const types = ['career', 'capital', 'experience', 'personal', 'purchases', 'health', 'business', 'product', 'finance']; types.forEach(type => { const progress = calculateProgress(type); const bar = document.getElementById(`progress-${type}`); const text = document.getElementById(`text-${type}`); const viz = document.getElementById(`viz-${type}`); if (bar) bar.style.width = `${progress}%`; if (text) text.textContent = `${Math.round(progress)}%`; if (viz) viz.textContent = `${Math.round(progress)}%`; // Update color based on progress if (progress < 30 && bar) { bar.style.background = '#ff2a2a'; bar.style.boxShadow = '0 0 10px #ff2a2a'; } }); } // Action Functions function addGoal(type) { if (appData[type].goals.length >= 5) return; appData[type].goals.push({ title: '', deadline: '', completed: false, subtasks: [] }); saveData(); renderStandardPage(type); } function deleteGoal(type, idx) { appData[type].goals.splice(idx, 1); saveData(); renderStandardPage(type); } function editGoal(type, idx) { document.getElementById(`${type}-goal-edit-${idx}`).style.display = 'block'; } function saveGoal(type, idx) { const title = document.getElementById(`${type}-goal-input-${idx}`).value; const date = document.getElementById(`${type}-goal-date-${idx}`).value; appData[type].goals[idx].title = title; appData[type].goals[idx].deadline = date; saveData(); renderStandardPage(type); } function toggleGoal(type, idx) { appData[type].goals[idx].completed = !appData[type].goals[idx].completed; saveData(); renderStandardPage(type); } function addSubtask(type, goalIdx) { const goal = appData[type].goals[goalIdx]; if (goal.subtasks.length >= 10) return; goal.subtasks.push({ title: '', deadline: '', completed: false, actions: [], trigger: '', notes: '' }); saveData(); renderStandardPage(type); } function deleteSubtask(type, goalIdx, subIdx) { appData[type].goals[goalIdx].subtasks.splice(subIdx, 1); saveData(); renderStandardPage(type); } function editSubtask(type, goalIdx, subIdx) { document.getElementById(`${type}-sub-edit-${goalIdx}-${subIdx}`).style.display = 'block'; } function saveSubtask(type, goalIdx, subIdx) { const title = document.getElementById(`${type}-sub-input-${goalIdx}-${subIdx}`).value; const date = document.getElementById(`${type}-sub-date-${goalIdx}-${subIdx}`).value; appData[type].goals[goalIdx].subtasks[subIdx].title = title; appData[type].goals[goalIdx].subtasks[subIdx].deadline = date; saveData(); renderStandardPage(type); } function toggleSubtask(type, goalIdx, subIdx) { appData[type].goals[goalIdx].subtasks[subIdx].completed = !appData[type].goals[goalIdx].subtasks[subIdx].completed; saveData(); renderStandardPage(type); } function addAction(type, goalIdx, subIdx, title) { if (!title) return; appData[type].goals[goalIdx].subtasks[subIdx].actions.push({ title: title, completed: false }); saveData(); renderStandardPage(type); } function deleteAction(type, goalIdx, subIdx, actIdx) { appData[type].goals[goalIdx].subtasks[subIdx].actions.splice(actIdx, 1); saveData(); renderStandardPage(type); } function toggleAction(type, goalIdx, subIdx, actIdx) { const actions = appData[type].goals[goalIdx].subtasks[subIdx].actions; actions[actIdx].completed = !actions[actIdx].completed; saveData(); renderStandardPage(type); } function updateTrigger(type, goalIdx, subIdx, value) { appData[type].goals[goalIdx].subtasks[subIdx].trigger = value; saveData(); } function updateNotes(type, goalIdx, subIdx, value) { appData[type].goals[goalIdx].subtasks[subIdx].notes = value; saveData(); } // Health Functions function updateHealthStat(stat, value) { appData.health.stats[stat] += value; saveData(); renderHealthPage(); } function calculateCalories() { const weight = parseFloat(document.getElementById('weight').value) || 70; const height = parseFloat(document.getElementById('height').value) || 175; const age = parseFloat(document.getElementById('age').value) || 30; const activity = parseFloat(document.getElementById('activity').value) || 1.2; // Mifflin-St Jeor Equation const bmr = 10 * weight + 6.25 * height - 5 * age + 5; const tdee = Math.round(bmr * activity); document.getElementById('calorie-result').textContent = `Р’Р°С€Р° РЅРѕСЂРјР°: ${tdee} РєРєР°Р»/РґРµРЅСЊ`; } function addRoute() { const name = document.getElementById('route-name').value; const distance = document.getElementById('route-distance').value; if (!name || !distance) return; if (!appData.health.routes) appData.health.routes = []; appData.health.routes.push({ name, distance, completed: false }); saveData(); renderRoutes(); } function renderRoutes() { const container = document.getElementById('routes-list'); if (!container || !appData.health.routes) return; container.innerHTML = appData.health.routes.map((route, idx) => `
${route.name}
${route.distance} РєРј
рџ—‘
`).join(''); } function toggleRoute(idx) { appData.health.routes[idx].completed = !appData.health.routes[idx].completed; saveData(); renderRoutes(); } function deleteRoute(idx) { appData.health.routes.splice(idx, 1); saveData(); renderRoutes(); } // Product Functions function updateProductAnswer(idx, value) { appData.product.answers[idx] = value; saveData(); updateProgress(); } function addProductAction() { appData.product.actions.push({ title: 'РќРѕРІРѕРµ РґРµР№СЃС‚РІРёРµ', deadline: '', completed: false }); saveData(); renderProductPage(); } function deleteProductAction(idx) { appData.product.actions.splice(idx, 1); saveData(); renderProductPage(); } function toggleProductAction(idx) { appData.product.actions[idx].completed = !appData.product.actions[idx].completed; saveData(); renderProductPage(); } function updateProductNotes(value) { appData.product.notes = value; saveData(); } // Finance Functions function translateExpense(key) { const translations = { regular: 'Р РµРіСѓР»СЏСЂРЅС‹Рµ РїР»Р°С‚РµР¶Рё', utilities: 'Р–РљРҐ', food: 'РџРёС‚Р°РЅРёРµ', transport: 'РўСЂР°РЅСЃРїРѕСЂС‚', entertainment: 'Р Р°Р·РІР»РµС‡РµРЅРёСЏ', family: 'РЎРµРјСЊСЏ', business: 'Р‘РёР·РЅРµСЃ', other: 'РРЅС‹Рµ Р·Р°С‚СЂР°С‚С‹' }; return translations[key] || key; } function updateFinance(type, key, value) { appData.finance[type][key] = parseFloat(value) || 0; saveData(); renderFinancePage(); } function updateExpense(key, subkey, value) { appData.finance.expenses[key][subkey] = parseFloat(value) || 0; saveData(); renderFinancePage(); } function updateFinanceValue(key, value) { appData.finance[key] = parseFloat(value) || 0; saveData(); renderFinancePage(); } function addOtherIncome() { appData.finance.income.other.push({ name: '', amount: 0 }); saveData(); renderFinancePage(); } function updateOtherIncome(idx, field, value) { appData.finance.income.other[idx][field] = field === 'amount' ? (parseFloat(value) || 0) : value; saveData(); renderFinancePage(); } function removeOtherIncome(idx) { appData.finance.income.other.splice(idx, 1); saveData(); renderFinancePage(); } function calculateTotalIncome() { const inc = appData.finance.income; let total = inc.salary + inc.freelance + inc.investments; inc.other.forEach(o => total += o.amount); return total; } function calculateTotalExpense() { let total = 0; Object.values(appData.finance.expenses).forEach(exp => { total += (exp.min + exp.max) / 2; }); return Math.round(total); } function calculateBalance() { return calculateTotalIncome() - calculateTotalExpense(); } function getFinanceAdvice() { const balance = calculateBalance(); const savings = appData.finance.savings; const debts = appData.finance.debts; if (balance < 0) return 'вљ пёЏ РЈРІРµР»РёС‡СЊС‚Рµ РґРѕС…РѕРґС‹ РёР»Рё СЃРѕРєСЂР°С‚РёС‚Рµ СЂР°СЃС…РѕРґС‹'; if (debts > savings) return 'рџ’Ў РџСЂРёРѕСЂРёС‚РµС‚: РїРѕРіР°С€РµРЅРёРµ РґРѕР»РіРѕРІ'; if (balance > 0 && balance < savings * 0.1) return 'рџ’° РћС‚РєР»Р°РґС‹РІР°Р№С‚Рµ РјРёРЅРёРјСѓРј 10% РґРѕС…РѕРґР°'; return 'вњ… Р¤РёРЅР°РЅСЃРѕРІРѕРµ СЃРѕСЃС‚РѕСЏРЅРёРµ СЃС‚Р°Р±РёР»СЊРЅРѕ'; } function drawFinanceChart() { const canvas = document.getElementById('finance-chart'); if (!canvas) return; const ctx = canvas.getContext('2d'); const width = canvas.width = canvas.offsetWidth; const height = canvas.height = canvas.offsetHeight; const income = calculateTotalIncome(); const expense = calculateTotalExpense(); const max = Math.max(income, expense, 1); // Clear ctx.clearRect(0, 0, width, height); // Draw bars const barWidth = 60; const spacing = 40; const startX = (width - (barWidth * 2 + spacing)) / 2; // Income bar const incHeight = (income / max) * (height - 60); ctx.fillStyle = '#00ff88'; ctx.fillRect(startX, height - incHeight - 30, barWidth, incHeight); // Expense bar const expHeight = (expense / max) * (height - 60); ctx.fillStyle = '#ff2a2a'; ctx.fillRect(startX + barWidth + spacing, height - expHeight - 30, barWidth, expHeight); // Labels ctx.fillStyle = '#e0f7ff'; ctx.font = '14px Rajdhani'; ctx.textAlign = 'center'; ctx.fillText('Р”РѕС…РѕРґС‹', startX + barWidth/2, height - 10); ctx.fillText('Р Р°СЃС…РѕРґС‹', startX + barWidth + spacing + barWidth/2, height - 10); // Values ctx.fillText(income + 'в‚Ѕ', startX + barWidth/2, height - incHeight - 40); ctx.fillText(expense + 'в‚Ѕ', startX + barWidth + spacing + barWidth/2, height - expHeight - 40); } // Notifications function checkNotifications() { const notifications = []; const now = new Date(); ['career', 'capital', 'experience', 'personal', 'purchases', 'health', 'business'].forEach(type => { appData[type].goals.forEach(goal => { if (goal.deadline && !goal.completed) { const deadline = new Date(goal.deadline); const diff = deadline - now; const days = Math.ceil(diff / (1000 * 60 * 60 * 24)); if (days < 0) { notifications.push({ type: 'danger', text: `${type}: РџСЂРѕСЃСЂРѕС‡РµРЅР° С†РµР»СЊ "${goal.title}"` }); } else if (days <= 3) { notifications.push({ type: 'warning', text: `${type}: РћСЃС‚Р°Р»РѕСЃСЊ ${days} РґРЅ. РґРѕ "${goal.title}"` }); } } }); }); const panel = document.getElementById('notification-list'); if (notifications.length > 0) { panel.innerHTML = notifications.map(n => `
${n.text}
`).join(''); document.getElementById('notifications').classList.add('active'); } } function toggleNotifications() { document.getElementById('notifications').classList.toggle('active'); } // Initialize updateProgress();
