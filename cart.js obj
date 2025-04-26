const cart = document.querySelector('.cart')
const container = document.querySelector('.container')
const productsContainer = document.querySelector('.products')

const products = {
	1: { id: 1, name: 'Laptop', price: 45000 },
	2: { id: 2, name: 'Mouse', price: 1500 },
	3: { id: 3, name: 'Keyboard', price: 2500 },
	4: { id: 4, name: 'Monitor', price: 12000 },
	5: { id: 5, name: 'Earpods', price: 3000 },
}

const cartList = {}

function createEl(obj) {
	const { id, name, price } = obj
	const container = document.createElement('div')
	container.innerHTML = `<p>Name: ${name}, Price: ${price}</p>`
	const addBtn = document.createElement('button')
	const removeBtn = document.createElement('button')
	addBtn.classList.add('addBtn')
	addBtn.dataset.id = id
	removeBtn.classList.add('removeBtn')
	removeBtn.dataset.id = id
	addBtn.innerHTML = `+`
	removeBtn.innerHTML = '-'
	container.appendChild(addBtn)
	container.appendChild(removeBtn)

	productsContainer.appendChild(container)
}

function createCartItem(id, item) {
	const container = document.createElement('div')

	container.innerHTML = `<p>Name: ${id}, Price: ${item.price}, Quantity: ${item.quantity}, total: ${item.total}</p>`
	const addBtn = document.createElement('button')
	const removeBtn = document.createElement('button')
	addBtn.classList.add('addBtn')
	addBtn.dataset.id = id
	removeBtn.classList.add('removeBtn')
	removeBtn.dataset.id = id
	addBtn.innerHTML = `+`
	removeBtn.innerHTML = '-'
	container.appendChild(addBtn)
	container.appendChild(removeBtn)
	console.log(container)
	cart.appendChild(container)
}

function listeners() {
	container.addEventListener('click', event => {
		if (event.target.classList.contains('addBtn')) {
			additem(event.target.dataset.id)
		}
		if (event.target.classList.contains('removeBtn')) {
			removeItem(event.target.dataset.id)
		}
	})
}

listeners()

Object.values(products).forEach(product => {
	createEl(product)
})

function updateCartUI() {
	cart.innerHTML = ''
	Object.entries(cartList).forEach(([id, item]) => {
		console.log(id, item)
		createCartItem(id, item)
	})
}

function additem(id) {
	if (!cartList[id]) {
		cartList[id] = {
			quantity: 1,
			price: products[id].price,
			total: products[id].price,
		}
	} else {
		cartList[id].quantity += 1
		cartList[id].total = products[id].price * cartList[id].quantity
	}

	updateCartUI()
}

function removeItem(id) {
	if (!cartList[id]) return
	if (cartList[id].quantity > 1) {
		cartList[id].quantity -= 1
		cartList[id].total = products[id].price * cartList[id].quantity
	} else {
		delete cartList[id]
	}
	updateCartUI()
}
